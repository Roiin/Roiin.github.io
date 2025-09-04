**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Shader

**Core Function:** Simulates a soft, cloth-like reflection at grazing angles, ideal for representing microscopic fibers or a layer of fine dust on a surface.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **Color (Input):** Defines the color of the sheen effect itself, which is often a brighter or more saturated version of the material's base color.
    
- **Roughness (Input):** Controls the quality of the sheen. Lower values produce a darker, fuzzier effect, while higher values create a brighter, more widespread reflection that can simulate a dusty surface.
    
- **Distribution (Property):** Selects the shading model. Ashikhmin provides a classic velvet look, while Microfiber is a newer, more physically-based model for fibrous surfaces.
    

**Practical Application:**  
This node is specifically designed to create the unique, soft sheen of fabrics like **velvet**. A standard diffuse shader looks flat and uninteresting, completely missing the characteristic glow that defines the material.

The problem is that velvet's appearance is dominated by the light catching its tiny, upright fibers, which only becomes visible at grazing angles (on folds and along the object's silhouette). A simple shader cannot replicate this view-dependent effect. The Sheen BSDF is the solution.

1. Start with a Diffuse BSDF to represent the base color of the fabric, which is typically a dark, desaturated color that appears when you look at the velvet head-on.
    
2. Add a Sheen BSDF. Set its Color to a bright, saturated version of your desired sheen color (e.g., a rich crimson for red velvet).
    
3. Combine these two shaders using an Add Shader node. This will layer the sheen effect on top of the dark diffuse base.
    
4. The result is a convincing velvet material. The surfaces facing the camera will be dark, showing the Diffuse color, but as the surface curves away, the Sheen BSDF will activate, creating a soft, luminous glow along the edges and folds. This perfectly mimics how light interacts with fibrous cloth and is the key to creating a believable velvet effect.