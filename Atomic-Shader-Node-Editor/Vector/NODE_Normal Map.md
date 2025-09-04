**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Interprets the RGB color data from a normal map image texture and converts it into perturbed normal vectors, allowing for the addition of high-frequency, baked surface detail.

**Key Properties & Settings:**

- **Normal (Output):** The primary output. This provides the modified normal vector and must be connected to the Normal input of any BSDF shader (e.g., Principled BSDF).
    
- **Color (Input):** The input where the normal map Image Texture is connected.
    
- **Strength (Input):** A simple multiplier that controls the intensity or depth of the normal map effect.
    
- **Space (Property):** Determines the coordinate system the normal map was baked in. Tangent space is the industry standard for game assets and character models as it works correctly with deforming meshes. Object space is for static objects.
    
- **UV Map (Property):** Allows you to specify which UV map to use for orienting the tangent space. This must match the UV map used by the Image Texture node.
    
- **CRITICAL WORKFLOW:** The Image Texture node containing the normal map must have its Color Space set to Non-Color. Using the default sRGB will produce incorrect results.
    

**Practical Application:**  
This node is the standard and most efficient way to render high-resolution detail onto a low-polygon model. Imagine you have a highly detailed sculpt of a character's skin, complete with pores and fine wrinkles. Rendering this high-poly model directly is computationally expensive.

The problem is how to capture all that fine surface detail onto a simpler, low-poly, animation-friendly model. The solution is to bake a "Normal Map" from the high-poly sculpt and then apply it to the low-poly model using the Normal Map node.

1. In a separate process, you would "bake" the surface normals from your high-poly sculpt onto the UVs of your low-poly model, creating a purple-ish normal map image.
    
2. In the shader for the low-poly model, add an Image Texture node and load this normal map. Critically, set its Color Space to Non-Color.
    
3. Add a Normal Map node. Connect the Color output of the Image Texture to the Color input of the Normal Map node.
    
4. Connect the Normal output of the Normal Map node to the Normal input of your Principled BSDF (which would be used to create the **stylized skin** material).
    
5. The result is that your simple, low-poly model now appears to have all the intricate detail of the original multi-million-polygon sculpt. The lighting will interact with the surface as if the pores and wrinkles were physically there, providing immense visual fidelity at a fraction of the performance cost. This is the fundamental workflow for creating detailed characters and assets for games and animation.