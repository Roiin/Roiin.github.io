**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Creates a reflective, specular surface, simulating materials ranging from perfect mirrors to rough metals and the glossy coating on plastics.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **Roughness (Input):** The most important control for the reflection's quality. A value of 0.0 creates a perfectly sharp, mirror-like reflection. As the value increases, the reflections become blurrier and softer, simulating a matte or sandblasted finish.
    
- **Color (Input):** Defines the color of the reflections. For non-metallic glossy coatings (like varnish), this should be white. For metals, it should be set to the metal's color (e.g., a yellow/orange for gold).
    
- **Anisotropy [Cycles Only]:** Stretches the highlights to simulate surfaces with fine parallel grooves, like brushed metal or spun metal. A value of 0 is a standard circular highlight.
    
- **Tangent [Cycles Only]:** An input used in conjunction with Anisotropy. It takes a direction vector (usually from a Tangent node) to control the orientation of the stretched anisotropic highlights.
    
- **Distribution:** The microfacet model used for calculating rough reflections. Multiscatter GGX is the most modern and physically accurate option, preventing energy loss (darkening) at higher roughness values.
    

**Practical Application:**  
While the Principled BSDF handles most materials, the Glossy BSDF is invaluable when you need precise control over reflections, especially for creating brushed metals. Imagine creating the surface of a stainless-steel appliance, which has a distinct "brushed" finish where highlights stretch into lines instead of dots.

The problem is that a standard reflection is isotropic (uniform in all directions) and creates round highlights. This looks like polished steel, not brushed steel. The Glossy BSDF is the solution for creating this anisotropic effect.

1. Start with a Glossy BSDF node. Set the Color to a light gray for steel and the Roughness to a low value like 0.15.
    
2. In Cycles, increase the Anisotropy value to something like 0.8. You will immediately see the specular highlights stretch into ovals.
    
3. To control the direction of the brushing, you must define a tangent. Add a Tangent node (set to UV Map) and connect its Tangent output to the Glossy BSDF's Tangent input.
    
4. Assuming you have a UV map where the UVs are aligned straight, the highlights will now stretch into clean lines, perfectly following the direction of your UVs. This creates a highly realistic brushed metal effect that is impossible to achieve with a basic glossy shader.