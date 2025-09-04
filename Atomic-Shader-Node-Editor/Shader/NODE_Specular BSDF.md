**Editor:** Shader Editor  
**Engine(s) Supported:** [Eevee Only]  
**Node Group:** Shader

**Core Function:** An Eevee-exclusive, all-in-one shader that uses the traditional "specular workflow" for creating materials, offering a performance-focused alternative to the Principled BSDF.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **Base Color (Input):** Defines the underlying diffuse color of the material. Unlike the Principled BSDF, this color does not affect the reflections of metallic surfaces.
    
- **Specular (Input):** The core of the specular workflow. This input controls both the intensity (as a grayscale value) and the color of the reflections directly. For dielectrics (like plastic), this is typically a shade of gray. For metals, it would be the metal's color.
    
- **Roughness (Input):** Controls the sharpness of both the diffuse and specular components. A value of 0.0 creates sharp, clear reflections, while higher values create a blurrier, more matte surface.
    
- **Clear Coat (Input):** Adds an additional, simple white specular layer on top of the base material. Ideal for simulating a varnish or clear-coat finish.
    
- **Transparency (Input):** Provides a simple transparency control that works with Eevee's Alpha Blend modes, but does not perform physical light refraction like glass.
    

**Practical Application:**  
This node is excellent for creating materials in Eevee where performance and direct artistic control are more important than strict physical accuracy. It is particularly well-suited for **stylized skin** on a cartoon character or vinyl figurine.

The problem is that the Principled BSDF is designed for realism, meaning a material's reflections are physically determined by its IOR and metallic properties. For a stylized look, you might want the skin to have a specific, non-physical highlight color—perhaps a cool blue tint—regardless of the lighting. This is difficult to achieve with the Principled shader. The Specular BSDF is the solution.

1. Set the Base Color to the character's main skin tone (e.g., a warm peach color).
    
2. Instead of tweaking IOR or metallic values, you can directly control the highlight. In the Specular input, select a light, desaturated blue color.
    
3. Adjust the Roughness to control the size and softness of this blueish highlight, creating anything from a tight, toy-like sheen to a soft, broad glow.
    
4. The result is a material that follows the artist's exact color choices rather than the laws of physics. The Specular BSDF decouples the diffuse color from the reflection color, giving you direct and intuitive control over the final look, which is perfect for achieving a specific artistic style in Eevee.