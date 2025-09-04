**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Color

**Core Function:** Blends two input colors or textures together using a variety of mathematical operations (blend modes) and a factor to control the mix.

**Key Properties & Settings:**

- **Result (Output):** The final, blended color.
    
- **Blend Mode (Mix):** The dropdown menu that selects the mathematical operation used to combine the two colors. Mix is a simple linear blend, while powerful modes like Multiply, Overlay, and Add provide distinct ways to layer textures.
    
- **Fac (Input):** The "Factor" input, which controls the strength of the mix. For the standard Mix blend mode, a value of 0.0 uses only Color A, 1.0 uses only Color B, and grayscale values in between create a blend. For other blend modes, it controls the overall opacity of the effect.
    
- **A / B (Inputs):** The two color/texture inputs to be blended.
    
- **Clamp Result (Property):** A checkbox that, when enabled, clamps the output color values to the standard 0.0 to 1.0 range. This is important for preventing non-physically-correct "super-white" or "super-black" values from being fed into a shader.
    

**Practical Application:**  
This node is essential for layering textures realistically. While the default Mix is useful, the Multiply blend mode is perfect for adding grime or stains to a surface. Imagine you have a clean **wood grain** texture, and you want to add a layer of dark, oily grime.

The problem is that if you use the standard Mix mode, it will simply fade between the clean wood and the grime, making the wood look semi-transparent, which is incorrect. The grime should darken the wood, not replace it. The Mix Color node's Multiply mode is the solution.

1. Start with your clean wood grain image texture. This will be the A input.
    
2. Create a procedural grime texture using a Noise Texture. For this to work, the grime texture should be mostly white with darker gray patches. This will be the B input.
    
3. Add a Mix Color node and set its blend mode to Multiply.
    
4. Connect the wood texture to A and the grime texture to B. Set the Fac to 1.0.
    
5. The Multiply operation darkens the base color (A) using the values from the top color (B). Where the grime texture is white (value of 1), the wood color is multiplied by 1 and remains unchanged. Where the grime texture is dark gray (e.g., a value of 0.2), the wood color's value is multiplied by 0.2, making it significantly darker.
    
6. This creates a much more convincing effect, as if a dark stain has soaked into the wood, rather than just being painted opaquely on top.