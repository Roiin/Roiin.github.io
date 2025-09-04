**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Calculates a reflection-to-refraction ratio based on the viewing angle, simulating how non-metallic surfaces become more reflective at grazing angles.

**Key Properties & Settings:**

- **Factor (Output):** The primary output. It provides a grayscale mask where white represents grazing angles (high reflectivity) and black represents angles facing the camera (low reflectivity). This is typically plugged into the Fac of a Mix Shader.
    
- **IOR (Input):** Stands for Index of Refraction. This crucial value dictates the strength and curve of the effect. It should be set to the real-world IOR of the material you are simulating (e.g., Water: 1.33, Glass: 1.5, Diamond: 2.4).
    
- **Normal (Input):** Allows you to connect a bump or normal map. This ensures the fresnel effect correctly follows the micro-surface details of your material, which is critical for realism.
    

**Practical Application:**  
This node is essential for creating virtually all realistic dielectric (non-metal) materials, from water to plastic to varnish. Consider creating a material for polished **wood grain**, which has a diffuse, woody base and a shiny, clear-coat finish.

The problem is that a simple mix of diffuse and glossy shaders looks fake, like plastic. You need the glossy reflections to appear strongest at the edges and fade when viewed head-on, just like real varnish. The Fresnel node is the solution.

1. Create two shaders: a Diffuse BSDF (or a Principled BSDF with high roughness) for the base wood material, and a Glossy BSDF for the clear-coat varnish.
    
2. Use a Mix Shader to combine them, with the Diffuse shader in the top slot and the Glossy in the bottom.
    
3. Add a Fresnel node and connect its Factor output to the Fac input of the Mix Shader.
    
4. Set the Fresnel node's IOR to approximately 1.5, a common value for varnish.
    
5. The result is a convincing clear-coat effect. When you look directly at the wood, you see the diffuse texture. As you view the object from a glancing angle, the glossy varnish reflections become prominent, perfectly simulating a lacquered surface.