**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides specific information about hair strands or geometry node curves, such as position along the strand, thickness, and a random value per strand.

**Key Properties & Settings:**

- **Intercept (Output):** Provides a black-to-white gradient that runs along the length of each individual curve, starting with 0 (black) at the root and ending with 1 (white) at the tip.
    
- **Random (Output):** Assigns a unique, random grayscale value (from 0 to 1) to each individual hair strand or curve.
    
- **Thickness (Output):** Outputs the thickness of the curve at the shading point, which can be used to drive other effects like translucency.
    
- **Is Strand (Output):** A boolean-like value that is 1 if the shader is being evaluated on a curve and 0 if on a regular mesh surface.
    

**Practical Application:**  
This node is essential for creating realistic hair. A character's hair is never a single, uniform color; it has subtle variations from strand to strand and often changes color from root to tip.

The problem is how to procedurally generate this natural variation. The Curves Info node is the solution.

1. Start with a Principled Hair BSDF shader as your base.
    
2. To create root-to-tip color variation (like sun-bleached ends or dyed hair growing out), connect the Intercept output to a ColorRamp node. Set the ColorRamp's left color to a dark "root" color and the right color to a lighter "tip" color. Plug the ColorRamp's output into the Color input of the Hair BSDF.
    
3. To create variation between strands, connect the Random output into the Fac of a Mix Color node. This allows you to blend the primary hair color with a slightly lighter or darker variant, ensuring each strand has a subtly different hue.
    
4. By combining these two techniques, you can achieve a highly realistic hair material where each strand has a unique color that also fades naturally from root to tip, moving far beyond a flat, artificial look.