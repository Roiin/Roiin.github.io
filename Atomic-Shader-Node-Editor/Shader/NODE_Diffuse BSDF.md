**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Creates a perfectly matte, non-reflective surface that scatters light uniformly in all directions.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **Color (Input):** Defines the base color of the material.
    
- **Roughness [Cycles Only]:** Controls the micro-roughness of the surface. A value of 0.0 creates a classic, ideal matte (Lambertian) surface. As the value increases, it transitions to the Oren-Nayar model, which realistically simulates rougher, dustier surfaces like clay or concrete that appear flatter and brighter at grazing angles.
    
- **Normal (Input):** Socket for connecting bump or normal maps to add surface detail.
    

**Practical Application:**  
This node is the fundamental building block for any material that should not have specular highlights, such as chalk, unglazed pottery, or certain fabrics. It is particularly powerful for creating **stylized skin** for cartoon or anime characters.

The problem is that photorealistic skin shaders, with their complex layers of specularity and subsurface scattering, look out of place in a stylized production. You need a soft, simple surface that responds to light cleanly without any distracting glossy reflections. The Diffuse BSDF is the perfect solution.

1. Start with a Diffuse BSDF as the base of your material.
    
2. Connect your base skin tone texture or a simple RGB node to the Color input.
    
3. The result is a clean, readable surface that feels soft and organic without the complexity of a Principled BSDF. This shader provides the ideal canvas for stylized character work, where form and color are more important than photorealistic detail. It ensures that the character's features are clearly defined by light and shadow, fitting perfectly within a non-photorealistic art style.