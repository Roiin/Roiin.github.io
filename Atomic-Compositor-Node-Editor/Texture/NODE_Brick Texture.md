- **Editor:** Compositor Node Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates a procedural and highly customizable brick wall pattern, including controls for brick and mortar color, size, and layout variations.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** Input for the texture coordinates. If left unconnected, it uses the screen's generated coordinates.
        
    - **Color1 / Color2 (Sockets):** Sets the two primary colors that the bricks will be randomly chosen from.
        
    - **Mortar (Socket):** Sets the color of the gaps between the bricks.
        
    - **Scale (Socket):** Controls the overall size of the entire pattern.
        
    - **Mortar Size (Socket):** Defines the thickness of the gaps between bricks. A value of 0 means no gaps.
        
    - **Mortar Smooth (Socket):** Blurs the transition between the brick and the mortar, creating a softer, more weathered look.
        
    - **Bias (Socket):** Influences the random color selection. A value of -1 will use only Color1, +1 will use only Color2, and 0 gives an even mix.
        
    - **Brick Width / Row Height (Sockets):** Controls the aspect ratio of the bricks.
        
    - **Offset / Frequency (Properties):** Controls the staggering of the brick rows. A Frequency of 2 creates a standard running bond pattern.
        
- **Outputs:**
    
    - **Color (Socket):** The final, full-color brick pattern.
        
    - **Factor (Socket):** A black-and-white mask where the mortar is white and the bricks are black. This is an incredibly useful output for building more complex effects.
        
- **Practical Application:** While its name implies one use, the Brick Texture node is a versatile pattern generator for both textures and abstract effects.
    
    - **Molecular (Procedural Wall/Floor Textures):** This is its most direct use. By feeding randomized colors (e.g., from a Noise Texture) into the Color1 and Color2 inputs, you can create a varied and non-repeating brick or tile texture to use as a background or for motion graphics.
        
    - **Molecular (Abstract Grid Patterns):** By setting the Mortar Size to a small value and the Offset to 0, you can generate a perfect, non-staggered grid or checkerboard pattern. This is useful for creating sci-fi displays, mosaic effects, or simple backgrounds.
        
    - **Organic (Displacement and Weathering):** The Factor output is the key to realism.
        
        1. Take the Factor output (the mortar mask).
            
        2. Run this mask through a Blur node to soften it.
            
        3. Use this blurred mask as the input for a Displace node affecting your main Color output. This will make the mortar appear recessed, giving the brick pattern a 3D look.
            
        4. You can also use the Factor output to Mix in a different, grittier texture only in the mortar gaps, adding realistic dirt and grime.
            
    - **Organic (Glitching / Digital Tile Effect):**
        
        1. Generate a Brick Texture.
            
        2. Take the Color output and use a Displace node.
            
        3. For the Displace vector, use a White Noise texture.
            
        4. This "organism" will randomly offset each "brick" of the image, creating a shattered, glitching, or mosaic-reveal effect, especially when animated.