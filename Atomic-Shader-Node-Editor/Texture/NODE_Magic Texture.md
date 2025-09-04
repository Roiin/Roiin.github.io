**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a complex, swirling, psychedelic pattern based on a repeating sine wave function, producing colorful and distorted results.

**Key Properties & Settings:**

- **Color (Output):** The primary output, providing a vibrant, multi-colored pattern.
    
- **Factor (Output):** A grayscale version of the pattern.
    
- **Depth (Property):** Controls the number of iterations for the function, adding detail and complexity to the pattern. Higher values create a more intricate result.
    
- **Distortion (Input):** Controls the amount of warping and swirling in the pattern. A value of 0 produces a more regular, grid-like pattern, while higher values create chaotic, fluid-like swirls.
    
- **Scale (Input):** Adjusts the overall size and frequency of the pattern.
    

**Practical Application:**  
This node's unique, colorful output is perfectly suited for simulating iridescent effects like soap bubbles or an oil slick on water. This phenomenon, known as thin-film interference, causes colors to shift and swirl based on the viewing angle.

The problem is that a standard Glass BSDF cannot create these shifting rainbow colors; it will just be clear or a single, uniform color. You need a texture that changes its appearance as you move the camera. The Magic Texture is the solution when driven by a view-dependent coordinate.

1. Start with a Glass BSDF to create the base transparent and reflective surface of a soap bubble.
    
2. Add a Magic Texture node. Adjust its Scale and Distortion to get a pleasing swirl of colors.
    
3. The critical step is to make the pattern view-dependent. Add a Texture Coordinate node and connect its Reflection output to the Vector input of the Magic Texture node. This forces the texture to be calculated based on the reflection angle.
    
4. To layer the color onto the bubble, connect the Magic Texture's Color output to the Color input of an Emission shader. Keep the Strength low (e.g., 1.0).
    
5. Use an Add Shader to combine the Glass BSDF with the Emission shader. This layers the swirling, view-dependent colors on top of the transparent surface.
    
6. The result is a convincing soap bubble. As you orbit the camera, the rainbow colors will shimmer, shift, and swirl across the surface, perfectly mimicking the real-world effect.