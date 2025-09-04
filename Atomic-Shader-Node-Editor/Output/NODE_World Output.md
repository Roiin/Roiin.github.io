**Editor:** Shader Editor (World Context)  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Output

**Core Function:** Serves as the final endpoint for the world's shader tree, defining the scene's background, environmental lighting, and global atmospheric effects.

**Key Properties & Settings:**

- **Surface (Input):** Defines the appearance of the world's background. This is where you connect a Background shader, which is often fed by an Environment Texture (HDRI) to provide realistic lighting and reflections for the entire scene.
    
- **Volume (Input):** Fills the entire world with a volumetric medium. Connecting a Volume Scatter or Principled Volume shader here is the standard method for creating global fog or atmospheric haze. Note: You cannot use both Surface and Volume simultaneously.
    
- **Target:** A property that allows you to specify if the output is for All render engines, or just for Cycles or Eevee, enabling you to create optimized world setups for each.
    

**Practical Application:**  
This node is the foundation for lighting any scene and making materials look believable. By default, a 3D scene is a black void with no light. An object with a reflective material, like a piece of polished chrome or a sphere of clear **ice**, will simply look black because it has nothing to reflect.

The problem is how to create a realistic environment that both lights the scene and provides something for reflective materials to interact with. The World Output node is the solution.

1. In the Shader Editor, switch the context from "Object" to "World".
    
2. The default setup is a Background shader connected to the World Output node's Surface input.
    
3. Add an Environment Texture node and load an HDRI (High Dynamic Range Image) of a real-world location, like a snowy field.
    
4. Connect the Color output of the Environment Texture to the Color input of the Background shader.
    
5. Now, the entire scene is illuminated by the light from the snowy field image. The sphere of **ice** is no longer a dark blob; it now has crisp, realistic reflections of the trees and sky from the HDRI. The World Output node has successfully taken this texture information and applied it as the global environment, which is the single most important step in achieving photorealistic renders.