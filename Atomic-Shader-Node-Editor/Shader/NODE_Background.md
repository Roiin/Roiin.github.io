**Editor:** Shader Editor (World Context)  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Defines the color and intensity of the scene's environmental light and visible background, acting as the primary source for ambient illumination and reflections.

**Key Properties & Settings:**

- **Background (Output):** The node's only output. This is a special shader type that must be connected to the Surface input of the World Output node.
    
- **Color (Input):** Sets the color of the background. This socket is most often driven by an Environment Texture (HDRI) to provide realistic, image-based lighting.
    
- **Strength (Input):** A multiplier for the brightness of the Color input. It controls the overall intensity of the environmental light, directly affecting global illumination and the brightness of reflections on all objects in the scene.
    

**Practical Application:**  
This node is the cornerstone of realistic lighting and is essential for making reflective materials look correct. Imagine you have created a perfect material for a chrome sculpture or a sphere of clear **ice**. In a default scene, you hit render, and the object comes out as a disappointing black shape.

The problem is that a reflective or refractive material has nothing to reflect or refract. The default 3D world is a black void. The Background node is the solution to create an environment for the material to interact with.

1. In the World's shader editor, the default setup connects a Background node to the World Output.
    
2. To achieve realistic lighting, add an Environment Texture node and load an HDRI image of a real-world location (e.g., a forest, a city street).
    
3. Connect the Color output of the Environment Texture to the Color input of the Background node.
    
4. Immediately, your scene is lit by this image. The **ice** sphere is no longer black; it is now reflecting the sky and refracting the trees from the HDRI. The Strength value on the Background node acts as a global dimmer switch, allowing you to increase or decrease the intensity of the environmental light without changing the texture. This node is the fundamental link that makes isolated materials feel like they are part of a larger world.