**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Generates an angle-dependent blending factor, providing an artist-friendly way to create effects that change as a surface turns away from the camera.

**Key Properties & Settings:**

- **Facing (Output):** Provides a linear gradient from 0 (facing the camera) to 1 (at a grazing angle). It's less physically accurate than Fresnel but is perfect for stylized effects like rim lighting or simulating cloth sheen.
    
- **Fresnel (Output):** A physically-based falloff similar to the Fresnel node, simulating how dielectric materials become more reflective at grazing angles. It is controlled by the Blend value instead of an IOR.
    
- **Blend:** The primary control for both outputs. A value of 0.5 provides a standard, balanced falloff. Lower values restrict the effect to only the most extreme grazing angles, while higher values make the effect more prominent across the entire surface.
    
- **Normal (Input):** Allows a bump or normal map to be connected, ensuring the effect correctly follows the micro-surface detail.
    

**Practical Application:**  
The Facing output of this node is uniquely suited for creating the characteristic sheen of fabrics like **velvet**. Real velvet appears darker when viewed head-on but shows a bright, saturated sheen on folds and along the silhouette where the fibers catch the light at a grazing angle.

The problem is that a single color shader cannot replicate this complex, view-dependent behavior; it will just look flat. The Layer Weight node is the solution.

1. Create a base Principled BSDF for the main, darker velvet color.
    
2. Create a second Principled BSDF for the brighter, more saturated sheen color.
    
3. Use a Mix Shader to blend between them, with the dark shader in the top slot and the sheen in the bottom.
    
4. Connect the Facing output of the Layer Weight node to the Fac input of the Mix Shader.
    
5. The result is a convincing velvet material. The parts of the object facing the camera will be dark, while the edges and folds will glow with the sheen color. By adjusting the Blend value, you can control the softness and width of this sheen, fine-tuning the material to look like anything from short-piled velour to a longer, fuzzier velvet.