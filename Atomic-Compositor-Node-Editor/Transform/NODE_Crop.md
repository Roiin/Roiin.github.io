- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** Cuts an image down to a smaller rectangular region, either by reducing the actual image dimensions or by making the area outside the crop region transparent.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be cropped.
        
    - **X / Y (Sockets):** Sets the coordinate of the **bottom-left** corner of the crop rectangle, in pixels.
        
    - **Width / Height (Sockets):** Sets the dimensions of the crop rectangle in pixels.
        
    - **Relative (Property Checkbox):** When checked, the X, Y, Width, and Height values are treated as a percentage of the original image dimensions instead of absolute pixels. This is useful for resolution-independent setups.
        
    - **Crop to Bounding Box (Property Button):** Automatically sets the crop values to the bounding box of the non-transparent pixels in the input image. This is extremely useful for optimizing renders.
        
- **Practical Application:** Cropping is a vital tool for composition, optimization, and isolating specific regions of an image for processing.
    
    - **Molecular (Re-framing / Composition):** This is its most direct artistic use. If you want to change the composition of your final render to be a tighter shot, you can add a Crop node at the end of your tree to re-frame the image.
        
    - **Molecular (Splitting an Image):** You can use multiple Crop nodes to split an image into different sections. For example, you could crop the left half of an image and the right half of an image onto two separate branches of the node tree, apply different effects to each half, and then re-combine them.
        
    - **Organic (Performance Optimization):** This is a critical technical use in professional VFX. Rendering effects like blur or glare over large areas of transparent pixels is a waste of processing time.
        
        1. Take your CG render (e.g., a character on a transparent background).
            
        2. Feed it into a Crop node and click Crop to Bounding Box. This shrinks the image's "working area" to only the pixels that actually contain the character.
            
        3. Now, apply your heavy effects (like Defocus or Glare) to this smaller, cropped image. The calculation will be significantly faster.
            
        4. After the effects are applied, use an Alpha Over or Set Alpha node with an appropriate background to place the cropped element back into the full-sized frame.
            
    - **Organic (Stabilization Workflow):** When you stabilize footage, it creates moving black borders. A common workflow is to stabilize, then crop away the maximum area of black border that appears, and finally scale the result back up to fill the frame. The Crop node is the essential middle step in this "Stabilize -> Crop -> Scale" molecule.