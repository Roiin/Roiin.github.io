- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- **Core Function:** Generates a random value (between 0 and 1) for every unique input coordinate. Unlike Noise Texture, which is smooth and organic, White Noise is harsh, chaotic, and completely incoherent from one pixel to the next. It is pure, digital static.
    
- **Key Properties & Settings:**
    
    - **Dimensions (Property):** Sets the "seed" type.
        
        - 1D: Uses the W input as a seed. Every unique W value gives a new random number.
            
        - 3D: Uses the Vector input as a seed. Every unique XYZ coordinate gives a new random number.
            
        - 4D: Uses both Vector and W as a combined seed. This is useful for getting different random patterns at the same location by changing the W value.
            
    - **Vector (Socket):** A 3D coordinate used as the seed in 3D and 4D modes.
        
    - **W (Socket):** A single value used as the seed in 1D and 4D modes.
        
- **Outputs:**
    
    - **Value (Socket):** A random grayscale value (0 to 1).
        
    - **Color (Socket):** A random color, where each RGB channel gets its own independent random value.
        
- **Practical Application:** White noise is not used for creating smooth, natural patterns. It is the "atom" of pure chaos and is used for things like static, random variation, and breaking up uniformity.
    
    - **Molecular (TV Static / Film Grain):** This is its most direct use.
        
        1. Create a White Noise texture.
            
        2. Mix this texture over your final image using an Overlay or Screen blend mode with a very low factor.
            
        3. To animate it, set the Dimensions to 4D and connect a Time or Scene Time node to the W input. This will generate a new random static pattern on every frame.
            
    - **Molecular (Star Field):** A simple and effective way to create a star field.
        
        1. Create a White Noise texture.
            
        2. Feed the Value output into a Color Ramp. Slide the black stop far to the right, creating a high-contrast map with only a few small white dots (the stars).
            
        3. Feed this into a Glare node set to Simple Star to give the brightest stars a twinkle.
            
    - **Organic (Randomizing Other Textures):** This is its most powerful application. You can use white noise to add random variation to the parameters of other procedural textures.
        
        1. You have a Brick Texture that looks too uniform.
            
        2. To give each brick a random color, first use a Vector Math (Snap) node on your texture coordinates to make each brick area have a single coordinate value.
            
        3. Feed this "snapped" vector into a White Noise node. The Color output will now be a random solid color for each brick.
            
        4. Use this random color map to drive the Color1 and Color2 inputs of your Brick Texture for a much more realistic, varied result.
            
    - **Organic (Procedural Glitch):** The harsh, blocky nature of White Noise is perfect for digital glitches. By snapping coordinates to a grid and then feeding them into a White Noise node, you can generate random offsets for a Displace node, causing blocks of your image to randomly jump around, creating a classic data corruption or "glitch" effect.