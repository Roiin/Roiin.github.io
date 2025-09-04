- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Provides a direct reference to a material data-block, allowing materials to be selected and used within the node tree.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    
    - **Material (Property):** A data-block selector to choose an existing material from the scene.
        
    - **Material (Socket - Output):** The selected material, ready to be connected to nodes that assign materials.
        
- **Practical Application:** This node is used to select a material which can then be assigned to a geometry using the Set Material node. It allows for the procedural assignment of different materials to different parts of a generated mesh, often controlled by a selection field.