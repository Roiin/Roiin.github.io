**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Simulates a physically-based glass material that both refracts light passing through it and reflects light from its surface based on the viewing angle (Fresnel).

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **IOR (Input):** The Index of Refraction. This is the most critical setting for realism, as it dictates how much light bends as it enters and exits the surface. It should be set to match the material you are simulating (e.g., Water: 1.33, Glass: 1.5, **Ice**: 1.31).
    
- **Roughness (Input):** Controls the clarity of the glass. A value of 0.0 results in perfectly clear, transparent glass. Increasing the value blurs both the refractions and reflections, creating the effect of frosted, etched, or sandblasted glass.
    
- **Color (Input):** Tints the light that passes through the glass. For perfectly clear glass, this should be set to pure white.
    
- **Distribution:** The microfacet model used for calculating rough reflections/refractions. Multiscatter GGX is the most modern and physically accurate option, preventing energy loss (darkening) at higher roughness values.
    

**Practical Application:**  
This node is essential for creating any transparent, refractive material. It is the ideal choice for creating realistic **ice**.

The problem with faking ice using a simple transparent shader is that it looks thin and insubstantial, like a ghost. It lacks the defining optical properties of a solid, frozen volume: the way it bends light and distorts the view behind it. The Glass BSDF is the solution.

1. Start with the Glass BSDF node. The single most important step is to set the IOR to 1.31, the physically accurate value for ice. This will immediately give the material the correct amount of refraction.
    
2. For clear, pure ice, leave the Color as pure white. For a slightly stylized or deep glacial ice, you can add a very faint blue tint.
    
3. To create a frosted look, simply increase the Roughness value. A small value (e.g., 0.1-0.2) will create a light frost, while higher values will make the ice more opaque and cloudy.
    
4. Connect the BSDF output to the Material Output. The result is a convincing ice material that correctly distorts the background, catches specular highlights, and feels like a solid, dense object.