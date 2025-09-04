- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates a random, discontinuous "white noise" value or color based on an input coordinate or ID. Unlike smooth Perlin noise, tiny changes in the input coordinate result in completely different, uncorrelated random outputs. This makes it the ideal choice for assigning unique random values to individual elements.
    
- **Key Properties & Settings:**
    
    - **Dimensions (Property):** Determines the type of input seed used for generating the random value:
        
        - **1D:** Uses the float W input.
            
        - **2D:** Uses the X and Y of the Vector input.
            
        - **3D:** Uses the full Vector input.
            
        - **4D:** Uses both the Vector and W inputs.
            
    - **Vector / W (Sockets - Input):** The coordinate or ID used as the "seed" to generate the random value.
        
    - **Value (Socket - Output):** A single, random float value between 0 and 1.
        
    - **Color (Socket - Output):** A random RGB color, where each channel is a unique random value between 0 and 1.
        
- **Practical Application:** This node is essential for giving unique properties to every instance in a collection, such as assigning a random color variation to each individual scale on a reptile.
    
    1. **The Goal:** You have a lizard model covered in hundreds of faces, each representing a scale. You want each scale to have a slightly different color tint to add realism and break up the uniformity.
        
    2. **The Problem:** Using a standard Noise Texture would create smooth, blurry patches of color that flow across many scales. You need each scale to have its own distinct random color.
        
    3. **The Solution:**
        
        - Use the White Noise Texture node set to 3D.
            
        - You need a unique seed for each face. The Position of the center of each face is a perfect unique 3D vector for this. Connect the Position node directly to the Vector input.
            
        - The Color output of the White Noise Texture now provides a completely random and unique color for every single face on the lizard.
            
        - Use a Store Named Attribute node to save this color as an attribute (e.g., "scale_tint").
            
    4. **The Result:** In the shader, you can mix this "scale_tint" attribute with your main scale color. The effect is that every single scale will have a subtle, unique color variation, completely different from its immediate neighbors. This creates a much more detailed and natural-looking skin than a uniform color or a smooth noise pattern could.