**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Simulates the physical bending (refraction) of light as it passes through a surface, but notably, does not include any surface reflections.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **IOR (Input):** The Index of Refraction. This is the most critical setting, as it dictates how much light bends when passing through the material. A value of 1.0 results in no bending.
    
- **Roughness (Input):** Controls the clarity of the refraction. A value of 0.0 creates a perfectly clear, see-through effect. Increasing the value blurs the light passing through, creating a frosted or sandblasted look.
    
- **Color (Input):** Tints the light that passes through the material. For a clear medium, this should be pure white.
    
- **Distribution (Property):** The microfacet model used for calculating rough refractions. GGX is the standard, while Beckmann is a legacy [Cycles Only] option.
    

**Practical Application:**  
This node is a fundamental building block for creating custom transparent materials when the all-in-one Glass BSDF is too restrictive. Imagine you want to create a custom glass or crystalline material for a fantasy prop. You need it to refract light like clear glass, but you want the surface reflections to have a distinct, non-physical color tint, perhaps a stylized blue or gold.

The problem is that the Glass BSDF can't do this; its reflection properties are physically linked to its transmission. The Refraction BSDF is the solution, allowing you to build the material component by component.

1. Start with a Refraction BSDF to handle the light passing through the object. Set its IOR to 1.5 (for glass) and leave its Color as pure white for a clear interior.
    
2. Next, add a Glossy BSDF to create the surface reflections. Set its Color to your desired stylized blue tint.
    
3. Add a Mix Shader to combine the two.
    
4. Crucially, connect a Fresnel node to the Fac input of the Mix Shader. This will ensure the material mixes between refraction (when viewed head-on) and reflection (at grazing angles) in a physically plausible way. The Refraction BSDF goes into the top slot, and the Glossy BSDF goes into the bottom slot.
    
5. The result is a highly art-directable material that behaves realistically but gives you complete, independent control over the refraction and reflection components—a feat impossible with simpler, pre-packaged nodes.