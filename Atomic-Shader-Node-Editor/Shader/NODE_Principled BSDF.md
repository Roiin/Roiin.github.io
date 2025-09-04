**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** An all-in-one, physically-based shader that can realistically simulate the vast majority of common materials by combining multiple layers like metal, glass, plastic, and skin into a single, user-friendly interface.

**Key Properties & Settings:**

- **Primary Controls:**
    
    - **Base Color:** Defines the material's underlying color for diffuse, metal, or subsurface components.
        
    - **Metallic:** A 0-to-1 slider that defines the material type. A value of 0 is a dielectric (non-metal) like plastic or **wood grain**. A value of 1 is a raw metal where the Base Color becomes the reflection color.
        
    - **Roughness:** Controls the microsurface detail, affecting the sharpness of reflections. A value of 0 creates a perfectly smooth, mirror-like surface, while a value of 1 creates a completely matte, diffuse surface.
        
- **Transmission (Glass & Liquids):**
    
    - **Transmission Weight:** A 0-to-1 slider that makes the object transparent. A value of 1 turns the material into a glass-like substance.
        
    - **IOR (Index of Refraction):** Controls how much light bends when passing through the transmissive material, essential for realistic glass, water, or **ice**.
        
- **Subsurface Scattering (Skin, Wax, etc.):**
    
    - **Subsurface Weight:** Blends from a standard opaque material to one where light penetrates the surface and scatters internally. Essential for creating soft materials like **stylized skin**, wax, or milk.
        
    - **Subsurface Radius:** A three-value vector (RGB) controlling how far each color of light scatters. For skin, a larger red value is used to simulate blood flow.
        
- **Layering Controls (Coat & Sheen):**
    
    - **Coat Weight:** Adds a thin, reflective clear-coat layer on top of all other components. Perfect for car paint, polished wood, or wet surfaces.
        
    - **Sheen Weight:** Adds a soft, cloth-like reflection at grazing angles, ideal for simulating the fuzzy look of fabrics like **velvet** or the dusty layer on other surfaces.
        
- **Other Key Inputs:**
    
    - **Emission Color/Strength:** Makes the surface emit light, turning it into a light source for effects like **molten lava**.
        
    - **Alpha:** Controls the material's overall transparency, typically used for cutout effects with an image texture.
        
    - **Normal:** The input for connecting bump and normal map textures to add fine surface detail.
        

**Practical Application:**  
This single node can create almost any material imaginable. Its true power lies in its built-in layers. Consider creating a high-quality car paint material. Car paint isn't a single substance; it's a colored/metallic layer with a highly reflective, protective clear coat on top.

The problem is that building this from separate Diffuse, Glossy, and Mix Shader nodes is complex and less physically accurate. The Principled BSDF solves this natively.

1. Set the main parameters for the paint layer. Choose a Base Color (e.g., deep red). Set Metallic to a medium value (e.g., 0.4) to simulate metallic flakes in the paint. Set the Roughness to a low-medium value (e.g., 0.2) for the paint's own finish. At this point, it looks like a semi-glossy red metal.
    
2. Now, add the clear coat. Simply increase the Coat Weight to 1.0. This instantly adds a new, physically-correct reflective layer on top of your base paint.
    
3. Fine-tune the clear coat's appearance. The Coat Roughness should be set very low (e.g., 0.03) to make it extremely shiny and reflective, distinct from the base layer's roughness.
    
4. The result is a convincing, multi-layered car paint material created with a single shader node. The Base Color, Metallic, and Roughness control the underlying paint, while the Coat parameters independently control the glossy top layer, demonstrating the node's power and efficiency.