**Editor:** Shader Editor  
**Engine(s) Supported:** Cycles Only  
**Node Group:** Script

**Core Function:** The Script Node empowers users to integrate custom shaders, written in the Open Shading Language (OSL), directly into Blender's node-based material system for the Cycles renderer. This provides a powerful method for technical artists and developers to achieve highly specific and complex shading effects that are not possible with the standard set of nodes.

**Key Properties & Settings:**

- **Mode:** This setting determines how the OSL shader is linked to the node.
    
    - **Internal:** The OSL shader code is stored within a Blender text data-block, and the compiled bytecode is saved directly in the node. This is ideal for sharing a .blend file with all necessary components included.
        
    - **External:** This mode allows you to link to an external .osl file. Blender will then automatically compile it to a .oso file in the same directory. You can also directly specify a path to a pre-compiled .oso file or a module name to be found in the shader search path.
        
- **Script Node Update:** This button reloads the OSL script, updating the node's input and output sockets to match any changes made to the shader's parameters.
    

**CRITICAL SETTING:** To utilize the Script node, you must first enable Open Shading Language in the Cycles render settings. This feature is compatible with CPU and OptiX rendering backends.

**Practical Application:**  
The Script node is invaluable when you need to create custom procedural textures or implement unique shading models. For instance, you can write an OSL shader to generate a procedural wood grain texture with intricate details that would be difficult to achieve with standard noise textures alone.

1. **Enable OSL:** In the Render Properties, ensure the render engine is set to Cycles and check the "Open Shading Language" box.
    
2. **Create a Script:** In the Text Editor, create a new text block and write your OSL shader. For example, a simple wood grain shader might use noise functions to create concentric rings and streaks.
    
3. **Add a Script Node:** In the Shader Editor, add a "Script" node (Shift+A > Script > Script).
    
4. **Link the Script:** In the Script node's properties, set the "Mode" to "Internal" and select your newly created text block from the dropdown menu.
    
5. **Update the Node:** Click the "Script Node Update" button to generate the input and output sockets based on your OSL code.
    
6. **Connect the Nodes:** Connect the outputs of your Script node (e.g., a "Color" output) to the inputs of other shader nodes, such as the "Base Color" of a Principled BSDF.
    
7. The result is a custom procedural material driven by your own code, offering a high degree of control and complexity. For production workflows, it's recommended to wrap script nodes within a node group to make them easier to manage and reuse across different blend-files.