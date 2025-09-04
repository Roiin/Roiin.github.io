**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee] (Note: Random Walk methods are Cycles Only)  
**Node Group:** Shader

**Core Function:** Simulates how light penetrates the surface of translucent materials, scatters internally, and then re-emerges at a different point, creating a soft, luminous, and often fleshy appearance.

**Key Properties & Settings:**

- **BSSRDF (Output):** The shader's output, representing the complex light scattering. This should be connected to a Mix Shader or Add Shader to combine with other surface properties.
    
- **Color (Input):** Defines the overall color of the material and influences the color of the scattered light.
    
- **Radius (Input):** The most critical input. This three-value vector (RGB) determines the average distance that each color of light travels beneath the surface before re-emerging. For example, for **stylized skin**, a higher red value in the radius makes light scatter further, creating a realistic reddish glow in thin areas like ears.
    
- **Scale (Input):** A global multiplier for the Radius values, allowing you to easily adjust the overall scattering depth without changing individual RGB components.
    
- **Subsurface Method:** Determines the algorithm used for scattering.
    
    - **Christensen-Burley:** A faster approximation, good for general subsurface effects.
        
    - **Random Walk:** (Cycles Only) A more physically accurate method, particularly good for thin or curved objects and preserving surface detail. Random Walk (Fixed Radius) and Random Walk are variations.
        
- **IOR [Cycles Only]:** Index of Refraction for the subsurface medium.
    
- **Anisotropy [Cycles Only]:** Controls the directionality of the internal scattering.
    

**Practical Application:**  
This node is essential for creating materials like wax, milk, marble, or **stylized skin**. These materials look fake and flat if treated as purely opaque surfaces.

The problem is that a standard Diffuse or Principled BSDF cannot replicate the soft, luminous look of translucent objects where light literally passes through the material, not just off its surface. You need light to scatter inside the object. The Subsurface Scattering node is the solution.

1. Start with a Diffuse BSDF (or Principled BSDF with 0 Metallic and 0 Transmission) for the basic surface. This will provide the primary color when light reflects directly off the surface.
    
2. Add a Subsurface Scattering node. Set its Color to a slightly desaturated version of your material's main color (e.g., a creamy white for **wax**).
    
3. Adjust the Radius values. For wax, you might use a uniform Radius across RGB (e.g., 0.05, 0.05, 0.05) to ensure light scatters equally for all colors, creating a soft, uniform translucency. Use the Scale input to fine-tune the overall depth of light penetration.
    
4. Connect both the Diffuse BSDF and the Subsurface Scattering node to a Mix Shader. You might use a Fresnel node as the Fac to make the subsurface effect more pronounced when light hits the surface head-on, blending with the more reflective Diffuse shader at grazing angles.
    
5. The result is a convincing wax material. Light will appear to bleed through the thinner parts of the object (like edges or areas facing a light source), creating a natural, soft glow and making the object feel solid yet translucent, which is impossible with a purely surface-based shader.