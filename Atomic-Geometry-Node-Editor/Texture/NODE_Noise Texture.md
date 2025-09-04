- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates fractal Perlin noise, a versatile and natural-looking procedural randomness. It can be configured from smooth, cloud-like patterns to rough, detailed surfaces, making it the workhorse for most organic procedural effects.
    
- **Key Properties & Settings:**
    
    - **Dimensions (Property):** Sets the evaluation space (1D, 2D, 3D, 4D). 4D is especially useful, as the W input can be used as a "seed" or can be animated over time to create evolving noise patterns.
        
    - **Vector (Socket - Input):** The 2D, 3D, or 4D coordinate at which to evaluate the noise.
        
    - **Scale (Socket - Input):** Controls the overall size of the noise pattern. Higher values make the pattern smaller and more frequent.
        
    - **Detail (Socket - Input):** Controls the number of noise layers (octaves) that are added together. Higher detail adds finer, smaller noise on top of the base pattern.
        
    - **Roughness (Socket - Input):** Controls the influence of the higher-detail octaves. Higher roughness makes the fine details more prominent, creating a rougher surface.
        
    - **Distortion (Socket - Input):** Adds a secondary noise pattern to warp the coordinates of the main noise, creating a swirling, turbulent effect.
        
    - **Factor (Socket - Output):** The primary output; a grayscale float value of the noise.
        
    - **Color (Socket - Output):** A color output where a different noise pattern is generated for each of the R, G, and B channels. This is great for creating more complex, multi-axis displacement or color variations.
        
- **Practical Application:** The Noise Texture is fundamental for adding natural imperfection and detail to any procedural model, such as creating the rough, bumpy skin of a rhinoceros.
    
    1. **The Base:** Start with a smooth base mesh of your rhinoceros. To hold the detail, it should be fairly high-poly, so use a Subdivision Surface node first.
        
    2. **The Goal:** To displace the surface to create the characteristic bumpy, wrinkled skin.
        
    3. Use a Set Position node. The displacement will be controlled by its Offset socket.
        
    4. Use a Noise Texture node set to 3D.
        
        - To create a base layer of large bumps, use one Noise Texture with a low Scale.
            
        - To create a layer of fine wrinkles, use a second Noise Texture with a much higher Scale and more Detail.
            
        - You can mix these two noise textures together using a Math or Vector Math node to create a multi-layered, complex pattern.
            
    5. To make the displacement happen outwards from the surface, multiply your final noise value by the mesh's Normal vector (using a Vector Math 'Scale' node).
        
    6. Connect this final vector to the Offset of Set Position.
        
    7. **The Result:** The smooth rhino mesh is now covered in a multi-layered, organic texture of bumps and wrinkles that looks far more natural and realistic than a single, uniform surface. The Noise Texture is the key ingredient for breaking up the "perfect" computer-generated look.