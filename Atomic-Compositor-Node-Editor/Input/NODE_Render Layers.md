- **Editor:** Compositor Node Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Acts as the primary input, bringing the rendered image and all associated data passes (e.g., Depth, Normals, Cryptomatte) from a specific 3D scene and view layer into the compositor. It is the source material for virtually all post-processing work.
    
- **Key Properties & Settings:**
    
    - **Scene (Property):** Selects which scene to pull render data from, allowing you to composite elements from multiple scenes in one node tree.
        
    - **View Layer (Property):** Selects the specific View Layer from the chosen scene. This is powerful for separating foreground, background, and effects elements.
        
    - **Image (Socket):** Outputs the main combined RGBA color image (the "beauty pass").
        
    - **Alpha (Socket):** Outputs the alpha channel of the render, defining its transparency.
        
    - **Depth (Socket):** Outputs a grayscale map where pixel values represent the distance from the camera. Essential for post-production depth of field.
        
    - **Mist (Socket):** Outputs the mist pass data, if enabled, for creating atmospheric effects.
        
    - **Normal (Socket):** Outputs the surface normals as colors, useful for advanced relighting effects.
        
    - **(Other Sockets):** This node is dynamic. Sockets will appear for any other render pass you enable in the View Layer Properties, such as Ambient Occlusion, Object ID, Cryptomatte, Shadow Catcher, etc.
        
- **Practical Application:** This is the starting point for nearly all visual effects and render enhancement workflows. The real power is unlocked by using the data passes.
    
    - **Molecular (Cinematic Depth of Field):** Combine the Image and Depth sockets with a Defocus node to create cinematic, non-destructive depth of field. This is much faster and more flexible than rendering DoF directly in-camera, allowing you to tweak the focus point and intensity after rendering.
        
    - **Molecular (Object-Specific Correction):** Use the Cryptomatte or Object ID output with an ID Mask node to generate a perfect mask for a specific object or material. This mask can then be used as the factor in a Color Balance node to, for example, make a single red flower in a field more vibrant without affecting anything else.
        
    - **Organic (Atmospherics & God Rays):**
        
        1. Feed the Mist pass into a Color Ramp to fine-tune its range and contrast.
            
        2. Use the result as the Factor in a Mix node to blend in a solid color, creating adjustable fog or haze.
            
        3. For god rays, you can mix this fog before the main Glare node (set to Fog Glow), which will cause bright areas (like a window) to cast beautiful, volumetric-looking light rays through the composited fog.
            
    - **Organic (Non-Destructive Relighting):** In advanced workflows, you can use the Normal pass combined with Color Dodge or Screen mix nodes to add fake "rim lights" or other lighting effects in the compositor. This allows you to adjust lighting on a character after the main render is complete, saving immense amounts of re-render time.