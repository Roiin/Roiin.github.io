- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Performs a simple, global adjustment to the overall brightness and contrast of an image, acting as a basic tool for tonal correction.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be adjusted.
        
    - **Bright (Socket):** An additive factor that uniformly increases or decreases the brightness of all pixels. Negative values darken the image.
        
    - **Contrast (Socket):** A scaling factor that pushes bright values brighter and dark values darker. Negative values reduce contrast, making the image appear flatter.
        
- **Practical Application:** While simple, it's a quick and effective tool for initial adjustments and for manipulating masks and data passes.
    
    - **Molecular (Primary Correction):** Its most direct use is to fix a render that is too dark or looks "washed out." A slight increase in Bright and Contrast can often be the first step in making a raw render "pop" before more nuanced color grading is applied.
        
    - **Molecular (Matte Tightening):** When you create a mask (e.g., from a Luma Key or Keying node), it might have soft, gray edges. By feeding this mask into a Brightness/Contrast node and increasing the Contrast significantly, you can "crush" the gray values towards pure black and white. This creates a harder, more precise matte, which is essential for clean compositing.
        
    - **Organic (Enhancing Specular Highlights):** To gain precise control over reflections:
        
        1. From your Render Layers node, take the Glossy Direct or Glossy Indirect pass (which contains only the specular highlights).
            
        2. Feed this pass into a Brightness/Contrast node. Increase the Contrast to make the highlights sharper and more intense.
            
        3. **Crucially**, you may need to add a Clamp or Map Range node after this to keep the values from becoming extreme.
            
        4. Use a Mix node set to Add to combine these enhanced highlights back onto your main Image pass. This "organism" gives you independent artistic control over the intensity of your reflections without having to re-render the 3D scene.
            
    - **Organic (Procedural Flash Effect):** To create a bright flash on screen for an impact or explosion:
        
        1. Place a Brightness/Contrast node on your main image stream.
            
        2. Use a Time Curve node to create a sharp spike in value (e.g., 0 up to 2 and back to 0) over just a few frames.
            
        3. Connect the Factor from the Time Curve into the Bright socket. The result is a perfectly timed, art-directed flash of light that affects the entire scene, all controlled procedurally by the curve.