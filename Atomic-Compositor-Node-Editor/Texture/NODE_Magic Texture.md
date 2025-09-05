- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- -**Core Function:** Generates a complex, colorful, and iridescent procedural pattern based on sine wave calculations. It excels at creating psychedelic, abstract, or "thin film interference" (oil slick) effects.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** Input for the texture coordinates.
        
    - **Scale (Socket):** Controls the overall size and frequency of the pattern. Higher values create more, smaller swirls.
        
    - **Distortion (Socket):** The key control for its characteristic look. It twists and warps the sine waves, creating chaotic, turbulent swirls. Low values are more regular, high values are more psychedelic.
        
    - **Depth (Property):** Sets the number of calculation iterations. Higher values add more complexity and finer detail to the pattern, but can be slower.
        
- **Outputs:**
    
    - **Color (Socket):** The full-color, iridescent pattern. This is the most commonly used output.
        
    - **Factor (Socket):** A grayscale representation of the pattern's intensity.
        
- **Practical Application:** The Magic Texture is almost exclusively used for artistic and stylized effects. It is not designed for photorealism (except for one specific case), but for creating eye-catching visuals.
    
    - **Molecular (Psychedelic Backgrounds):** This is its most direct use. By animating the Distortion value or by moving the texture coordinates over time (e.g., by animating a Mapping node), you can create vibrant, swirling, and constantly changing backgrounds for motion graphics, music visualizations, or sci-fi interfaces.
        
    - **Molecular (Thin Film Interference / Oil Slick):** This is a specific and powerful "molecule" for shaders, but the principle can be used in the compositor. The iridescent, rainbow-like patterns it creates are very similar to the effect of thin film interference on soap bubbles or oil slicks. By overlaying this texture with a Screen or Add blend mode onto a reflective surface, you can fake this complex physical phenomenon.
        
    - **Organic (Abstract Energy Fields or Auras):**
        
        1. Create a Magic Texture with a high Distortion.
            
        2. Use its Factor output as a displacement map for its own Color output. This will make the pattern appear to boil and warp in on itself.
            
        3. Feed the result into a Glare node set to Fog Glow to make the bright areas bloom.
            
        4. This "organism" creates a complex, glowing, and self-animating energy field that can be used for magical effects or sci-fi shields.
            
    - **Organic (Displacement and Distortion Maps):** The Factor output, while less colorful, is a complex and unique grayscale pattern. You can use it as the vector input for a Displace node to warp and distort other images or footage in a unique, swirling, and organic way that would be difficult to achieve with a standard Noise texture.