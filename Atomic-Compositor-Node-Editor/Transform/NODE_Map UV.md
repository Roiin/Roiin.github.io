- **Editor:** Compositor Node Editor  
- **Node Group:** Distort
    
- **Core Function:** Warps a 2D image so that it perfectly conforms to the UV map of an object in the rendered scene. It effectively allows you to apply a new texture, decal, or pattern to an object after it has been rendered.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The input for the new 2D texture you want to apply (e.g., from an Image or Texture node).
        
    - **UV (Socket):** The crucial data input. This must be connected to the UV render pass output from a Render Layers node. (Note: The UV pass is typically only available in Cycles).
        
    - **Filter Type (Property):** The interpolation method for the distortion. Anisotropic provides the highest quality, especially for textures viewed at an angle.
        
- **Outputs:**
    
    - **Image (Socket):** The final, warped texture, ready to be composited onto your render.
        
- **Practical Application:** This node is a post-production texturing tool. It's the "atom" for applying decals, fixing textures, or adding procedural details without needing to re-render the 3D scene.
    
    - **Important Context (Limitation):** This node applies the texture after all lighting and shading have been calculated. The new texture will **not** receive shadows, cast shadows, or be affected by the scene's lighting in a physically correct way. Think of it as applying a perfect "sticker" or "decal" to your render, not as a replacement for 3D texturing.
        
    - **Molecular (Applying a Decal or Logo):** This is its most common and direct use.
        
        1. In your View Layer Properties, under Passes, enable the UV pass.
            
        2. In the compositor, connect the UV output from your Render Layers node to the UV input of the Map UV node.
            
        3. Load your logo or decal with an Image node (it must have an alpha channel) and connect it to the Image input of the Map UV node.
            
        4. Use an Alpha Over node to composite the Image output from the Map UV node on top of your main render. The logo will now be perfectly "stuck" to the surface of your object, following its UV layout.
            
    - **Organic (Object-Specific Re-texturing):** To apply a texture to only one object in a complex scene:
        
        1. First, use a Cryptomatte node to create a perfect mask of your target object.
            
        2. Generate your warped texture using the Map UV node as described above.
            
        3. Use a Set Alpha node. Connect the warped texture to the Image socket and the Cryptomatte matte to the Alpha socket. This ensures the new texture only exists where the target object is.
            
        4. Alpha Over this result onto your original render. This "organism" allows for precise, isolated re-texturing of individual elements in a scene.
            
    - **Organic (Procedural Weathering):** Instead of an image, you can use a procedural texture to add details.
        
        1. Create a "grunge map" using a Noise Texture and a Color Ramp.
            
        2. Feed this procedural grunge into the Image input of the Map UV node. The output will be a grunge pattern perfectly mapped to your object's UVs.
            
        3. You can then use this as a mask to Mix a rust or dirt color over your original render, adding a layer of procedural weathering in the compositor. You would still use a Cryptomatte mask to ensure this effect is limited to the correct object.