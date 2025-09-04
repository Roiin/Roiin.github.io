**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Defines a direction vector used by the Anisotropic BSDF to orient and stretch specular highlights, simulating surfaces with fine parallel grooves or fibers.

**Key Properties & Settings:**

- **Tangent (Output):** The primary output. This vector must be connected to the Tangent input of an Anisotropic BSDF to have any effect.
    
- **Direction Type:** The main setting that determines how the tangent direction is generated.
    
    - **Radial:** Creates a circular pattern around the object's X, Y, or Z axis. Perfect for creating the "spun" look on objects like metal knobs or the bottom of a cooking pot.
        
    - **UV Map:** Aligns the tangent direction with the V-axis (the vertical direction) of the object's active UV map. This provides precise, artist-controlled alignment for effects like brushed metal sheets or **wood grain**.
        

**Practical Application:**  
This node is specifically designed to create anisotropic materials, most famously brushed metal. A standard glossy shader produces perfectly circular highlights, which is incorrect for a surface that has microscopic grooves running in a single direction.

The problem is how to tell the shader which direction these grooves are running in to accurately stretch the highlights. The Tangent node is the solution.

1. Start by using an Anisotropic BSDF instead of a standard Glossy BSDF or Principled BSDF (or by setting the Anisotropic value on the Principled BSDF to 1.0).
    
2. Add a Tangent node and connect its Tangent output to the Tangent input of the Anisotropic BSDF.
    
3. To create a flat, brushed steel sheet, you would first UV unwrap the object so the UVs are straight and aligned. Then, set the Tangent node's Direction Type to UV Map. The highlights will now stretch correctly along the direction of the brushing.
    
4. Alternatively, to create a "spun" metal dial, you would set the Direction Type to Radial and choose the axis that points out from the face of the dial (e.g., Z-axis). This will create circular highlights, perfectly simulating a lathed or spun finish.