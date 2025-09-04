**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides camera-relative information, such as distance and viewing angle, for each point being shaded on a surface.

**Key Properties & Settings:**

- **View Distance (Output):** The most commonly used output. It measures the direct, straight-line distance from the camera's origin to the point being shaded.
    
- **View Z Depth (Output):** Measures the perpendicular distance from the camera's plane to the shading point. It is essential for effects that need to align with the camera's view, like creating a mist pass.
    
- **View Vector (Output):** Provides the direction vector from the camera to the shading point. Useful for creating custom view-dependent effects.
    

**Practical Application:**  
This node is excellent for creating material-based atmospheric effects. Imagine you are building a vast, frozen landscape covered in **ice**. You want the ice in the distance to appear foggier and less detailed to enhance the sense of scale and depth, without relying on a global world fog.

The problem is how to make the material itself aware of its distance from the camera. The Camera Data node is the solution.

1. Create your primary Principled BSDF shader for the detailed, nearby ice.
    
2. Create a second, simpler shader to represent the "foggy" distant ice (e.g., a white, slightly emissive shader).
    
3. Use a Mix Shader node to blend between the "clear ice" and "foggy ice" shaders.
    
4. Connect the View Distance output of the Camera Data node into the Fac input of the Mix Shader.
    
5. To control the transition, insert a ColorRamp node between the Camera Data and Mix Shader nodes. By adjusting the handles on the ColorRamp, you can precisely define at what distance the fog begins to appear and at what distance the ice becomes fully obscured. This creates a powerful, art-directable distance haze that is baked directly into the material.