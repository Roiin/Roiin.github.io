**Editor:** Shader Editor (Light Context)  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Output

**Core Function:** Serves as the final endpoint for a Light object's shader tree, defining the color, intensity, and texture of the emitted light.

**Key Properties & Settings:**

- **Surface (Input):** The primary and only input. This socket expects a shader with an emission component (typically an Emission shader) to define the light's characteristics.
    
- **Target:** A property that allows you to specify if the output is for Cycles or Eevee, though the node is currently only functional in Cycles.
    

**Practical Application:**  
This node unlocks the ability to create complex, textured lighting, often called "gobos" or "cookies." A standard spot light casts a uniform, perfectly circular cone of light, which can look artificial. Imagine you need to simulate the light from a slide projector casting an image onto a wall, or the dappled light filtering through a stained-glass window.

The problem is that a light's basic settings (color, power) cannot create these intricate patterns. The Light Output node is the solution, as it allows you to use textures to control the light itself.

1. Select a Spot Light in your scene. In its Object Data Properties (the green light bulb icon), enable Use Nodes.
    
2. The Shader Editor will now show a simple network: an Emission shader plugged into the Light Output node's Surface input.
    
3. Add an Image Texture node and load a black-and-white image, for instance, the silhouette of a window frame.
    
4. To project this texture, connect a Texture Coordinate node's Normal output to the Vector input of the Image Texture.
    
5. Connect the Color output of the Image Texture into the Strength input of the Emission shader.
    
6. Now, the spot light acts as a projector. The white areas of the texture will allow light to pass through at full strength, while the black areas will block the light entirely, effectively casting the shadow of the window frame onto any surface it hits. This technique is fundamental for creating realistic and dramatically shaped lighting.