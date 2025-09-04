**Editor:** Shader Editor  
**Engine(s) Supported:** [Eevee Only]  
**Node Group:** Converter

**Core Function:** Converts the calculated lighting and shading result of a BSDF shader into simple RGB color data, allowing it to be manipulated by standard color nodes after lighting has been calculated.

**Key Properties & Settings:**

- **Color (Output):** The primary output. It provides the final lit color of the input shader as a standard yellow color socket.
    
- **Alpha (Output):** Provides the alpha channel from the input shader, if any.
    
- **Shader (Input):** The input for a BSDF shader (e.g., Diffuse BSDF, Principled BSDF).
    

**Practical Application:**  
This node is a cornerstone of advanced Non-Photorealistic Rendering (NPR) and cel-shading in Eevee. It provides a powerful alternative to the Toon BSDF for creating highly flexible, custom toon shaders.

The problem with the standard Toon BSDF is that its shading is limited to simple bands. You might want a more complex gradient, for example, a shadow that transitions from blue to purple. This is impossible to do before lighting is calculated. You need a way to modify the result of the shading. The Shader to RGB node is the solution.

1. Start with a simple Diffuse BSDF as your base shader. This will calculate the standard, smoothly-lit surface.
    
2. Connect this Diffuse BSDF to the Shader input of the Shader to RGB node.
    
3. The Color output of this node now contains the final, lit result as a grayscale gradient (since the input diffuse color was likely gray).
    
4. Connect this grayscale output to the Fac input of a ColorRamp node.
    
5. In the ColorRamp, you can now define your custom shading ramp. You could place a light color on the right (for the lit areas), a mid-tone in the middle, and a dark shadow color on the left. You could even add complex colors, like a cool blue for the shadow and a warm yellow for the light.
    
6. The final step is to make this color visible. Since the data is now RGB and not a shader, it must be plugged into an Emission shader (with Strength set to 1.0) or directly into the Material Output's Surface socket if Emission is not desired.
    
7. The result is a completely custom toon shader. The Diffuse BSDF provides the lighting information, and the ColorRamp provides the artistic color and banding, giving you far more creative freedom than a standard toon shader.