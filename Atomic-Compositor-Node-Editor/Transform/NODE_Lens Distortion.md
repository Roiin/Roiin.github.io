- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** Simulates the optical imperfections found in real-world camera lenses, such as barrel/pincushion distortion and chromatic aberration (color fringing). It is essential for adding a final layer of photorealism or for matching the distortion of a camera used to film a background plate.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Projector (Property Checkbox):** A legacy option, typically left unchecked.
        
    - **Jitter (Property Checkbox):** Uses a faster, but lower-quality (noisier) algorithm for the distortion. Useful for previews.
        
    - **Fit (Property Checkbox):** Automatically scales the image to hide the black, empty areas that are created by the distortion.
        
- **Main Controls:**
    
    - **Distort (Socket):** The primary control for barrel and pincushion distortion.
        
        - **Positive values** create **barrel distortion**, making the image appear to bulge outwards from the center, like a fisheye lens.
            
        - **Negative values** create **pincushion distortion**, making the image appear to pinch inwards at the center.
            
    - **Dispersion (Socket):** The primary control for chromatic aberration. It separates the red, green, and blue channels slightly, creating a rainbow-colored fringe effect that is most noticeable at the edges of the frame and in high-contrast areas.
        
- **Practical Application:** This is a "final touch" node. You add it near the end of your composite to break the perfect, straight lines of a CG render and make it feel like it was filmed through a real piece of glass.
    
    - **Molecular (Adding Photorealism):** This is its most common use.
        
        1. Add a Lens Distortion node near the end of your node tree, just before the final Composite node.
            
        2. Add a very small positive Distort value (e.g., 0.015) to simulate the subtle barrel distortion common in many lenses.
            
        3. Add a very small Dispersion value (e.g., 0.008) to create a subtle chromatic aberration.
            
        4. This simple "molecule" instantly makes a sterile CG render feel more like a real photograph by introducing the kinds of imperfections our eyes are accustomed to seeing from real cameras.
            
    - **Organic (Matching Live-Action Footage):** This is its critical VFX use. When compositing a CG element into a live-action shot, the CG will have perfectly straight lines, while the footage will have lens distortion. They won't match.
        
        1. **Workflow A (Distort CG):** Determine the distortion of the live-action plate. Apply the same distortion values to your CG element before you composite it.
            
        2. **Workflow B (Undistort Plate - Recommended):** This is the professional method. First, apply a Lens Distortion node to your live-action footage with negative values to remove the distortion and make it perfectly rectilinear. Composite your clean CG on top of this undistorted plate. Then, at the very end, add another Lens Distortion node with the original positive values to re-introduce the distortion to the entire composite. This ensures the CG and the plate are affected identically.
            
    - **Molecular (Fisheye / Security Camera Effect):** For a stylized effect, you can push the Distort value much higher (e.g., 0.2 to 0.5) to create a strong, obvious fisheye lens look, perfect for simulating security camera footage or a "point of view" shot from a character wearing a helmet.