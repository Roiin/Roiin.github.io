- **Editor:** Logic Node Editor
    
- **Node Group:** Nodes > Material
    
- **Core Function:** Sets the value of an input socket on a specific node within a material's shader node tree.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input.
        
    - **Material (Socket):** The target material.
        
    - **Node Name (Socket):** The name of the shader node to modify.
        
    - **Socket Name (Selector):** The name of the input socket to change.
        
    - **Value (Socket):** The new data to be assigned to the socket.
        
- **Practical Application:** The primary node for dynamically changing a material's appearance. Examples: making a character's armor glow by increasing the "Emission Strength", making a surface wet by decreasing its "Roughness", or changing an object's color by feeding a new vector into its "Base Color".