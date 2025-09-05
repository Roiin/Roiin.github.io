- **Editor:** Compositor Node Editor  
- **Node Group:** Mask
    
- **Core Function:** A revolutionary keying tool that generates incredibly accurate, anti-aliased mattes for specific objects, materials, or assets directly from the render data. It allows you to create perfect masks simply by clicking on the desired element in the final render, even through transparency and motion blur.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** A standard color input, typically your main beauty pass. This is only needed if you want to use the node's Image output.
        
    - **Source (Property):** Determines where to get the Cryptomatte data. Render uses the passes from the active render. Image is for loading an external multi-layer EXR file.
        
    - **Cryptomatte Layer (Property):** Selects which Cryptomatte pass to use (e.g., CryptoObject, CryptoMaterial, CryptoAsset).
        
    - **Add/Remove (Buttons):** The main interface. Click the + eyedropper, then click on an object in the Viewer node backdrop to add it to the matte. Click the - eyedropper to remove an object.
        
    - **Matte ID (Property):** A text field that lists the names of the selected objects/materials. Can be edited manually.
        
- **Outputs:**
    
    - **Image (Socket):** The input Image with the generated matte applied as an alpha channel.
        
    - **Matte (Socket):** The raw, high-quality, black-and-white grayscale matte. **This is the most powerful and flexible output.**
        
    - **Pick (Socket):** Outputs a colored visualization of the Cryptomatte data itself. This is useful for picking objects when the main render is too dark or complex.
        
- **Practical Application:** Cryptomatte has fundamentally changed the compositing workflow, making tasks that were once tedious and difficult incredibly simple and precise. It is the modern standard for object/material-based masking.
    
    - **Molecular (Perfect Object/Material Selection):** This is its core function.
        
        1. In View Layer Properties -> Passes, enable Cryptomatte Object and/or Material.
            
        2. After rendering, add a Cryptomatte node. Connect your main render to a Viewer node to see the backdrop.
            
        3. In the Cryptomatte node, click the + eyedropper and simply click on the object you want to isolate (e.g., a specific character's helmet).
            
        4. The Matte output now contains a perfect, anti-aliased mask of that helmet, which you can use to drive a Color Balance node to change its color, for example.
            
    - **Organic (Complex Secondary Color Correction):** Imagine you want to make all the chrome materials in a complex car render slightly more blue, and all the leather seats slightly less saturated.
        
        1. **Node 1 (Chrome):** Use a Cryptomatte node set to CryptoMaterial. Pick a chrome surface. The matte will select all objects with that same chrome material. Use this matte to drive a blue Color Balance adjustment.
            
        2. **Node 2 (Leather):** Use another Cryptomatte node set to CryptoMaterial. Pick a leather seat. Use this matte to drive a Hue/Saturation node to lower the saturation.
            
        3. By layering these adjustments, you can perform highly complex, non-destructive material changes in the compositor without ever re-rendering.
            
    - **Organic (Holdout Mattes for VFX):** Cryptomatte is perfect for creating "holdouts" (masks that block out parts of an effect).
        
        1. You have a render of a character walking. You want to add a large smoke effect behind them.
            
        2. Use a Cryptomatte node to generate a perfect matte of the character.
            
        3. Generate your smoke effect using a Noise Texture.
            
        4. Use the character's Cryptomatte as the Factor in a Set Alpha node applied to the smoke. This will "cut out" the character's shape from the smoke.
            
        5. Alpha Over the resulting smoke onto your background, then Alpha Over the original character on top of that. The smoke will now appear to be perfectly wrapping around behind them. This is far more accurate than manual rotoscoping.