**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Generates a black-and-white mask of the mesh's wireframe, highlighting the edges of its underlying polygons.

**Key Properties & Settings:**

- **Factor (Output):** The primary output. It provides a grayscale mask where faces are black and the edges between them are rendered as white lines.
    
- **Size:** Controls the thickness of the wireframe lines. This value is measured in world units unless Pixel Size is enabled.
    
- **Pixel Size:** When checked, the Size value is interpreted in pixels on the final rendered image. This ensures the wireframe lines maintain a consistent visual thickness regardless of how close or far the object is from the camera.
    

**Practical Application:**  
This node is ideal for creating stylized, sci-fi, or diagnostic materials. Imagine you want to create a holographic effect or a sci-fi energy shield that visibly traces the geometry of an object.

The problem is that a standard Emission or Transparent shader would just create a uniform glowing blob. You need the effect to be concentrated along the object's structural lines. The Wireframe node is the perfect solution.

1. Create two shaders: a Transparent BSDF to represent the empty space within the hologram, and a glowing Emission shader for the energy lines.
    
2. Use a Mix Shader to combine them.
    
3. Connect the Factor output of the Wireframe node directly into the Fac input of the Mix Shader.
    
4. Plug the Transparent BSDF into the top socket and the Emission shader into the bottom socket of the Mix Shader.
    
5. The result is a material where only the edges of the geometry emit light, while the faces remain completely see-through. By adjusting the Size property and the Emission color and strength, you can create a wide range of compelling holographic projections, force fields, or technical readouts directly on the surface of any object.