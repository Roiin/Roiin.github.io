- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- -**Core Function:** Generates a classic, perfectly uniform checkerboard pattern.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** Input for the texture coordinates. If left unconnected, it uses the screen's generated coordinates, creating a grid aligned with the X and Y axes.
        
    - **Color1 / Color2 (Sockets):** Sets the two alternating colors of the checker pattern.
        
    - **Scale (Socket):** Controls the size of the squares. A higher value results in more, smaller squares. A value of 2.0 would create a 2x2 grid if the input coordinates range from 0 to 1.
        
- **Outputs:**
    
    - **Color (Socket):** The final, full-color checker pattern.
        
    - **Factor (Socket):** A black-and-white mask of the pattern, where squares of Color1 are white and squares of Color2 are black.
        
- **Practical Application:** While simple, the Checker Texture is a crucial utility for creating grids, masks, and serving as a diagnostic tool.
    
    - **Molecular (Diagnostic UV Checker):** This is a classic technical use. To check if an object's UVs are unwrapped correctly or to visualize distortion in a Displace effect, you can temporarily apply a Checker Texture. The even, predictable pattern makes any stretching, pinching, or seams immediately obvious.
        
    - **Molecular (Tiled Floors and Backgrounds):** Its most direct artistic use is to create tiled floors or simple geometric backgrounds for motion graphics. By feeding a subtle Noise Texture into the Color1 and Color2 inputs, you can give the tiles a more organic, non-uniform appearance.
        
    - **Organic (Masking Alternate Strips):** You can use the Checker Texture to create a mask for applying an effect to every other row or column.
        
        1. To create horizontal stripes, use a Separate XYZ node on the input Vector and a Combine XYZ node, leaving the X input disconnected. This feeds only the Y coordinates into the Checker Texture, resulting in horizontal bands.
            
        2. You can then use the Factor output of this "stripe" texture as a mask to, for example, create a scanline effect or offset every other row of pixels with a Displace node.
            
    - **Organic (Procedural Glitch and Dithering):**
        
        1. Create a Checker Texture with a very high Scale to make a fine grid.
            
        2. Use a White Noise texture to randomly distort the Vector input of the Checker Texture.
            
        3. The result is a chaotic, glitchy pattern of squares that can be Multiplied or Added over footage to create a digital interference effect. This same high-frequency checker pattern can also be used to create dithering-style transitions when used as a mask.