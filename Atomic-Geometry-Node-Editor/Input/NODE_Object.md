- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Imports a selected object's data from the scene, providing its geometry and transform information to the node tree.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Object (Property):** A data-block selector to choose an object from the current scene.
        
    - **As Instance (Property):** A boolean toggle. If enabled, the object is brought in as a single instance, which is more memory-efficient. If disabled, its raw geometry is imported.
        
    - **Geometry (Socket - Output):** The mesh or curve data of the selected object.
        
    - **Location (Socket - Output):** A vector representing the object's world-space location.
        
    - **Rotation (Socket - Output):** A vector representing the object's Euler rotation.
        
    - **Scale (Socket - Output):** A vector representing the object's scale.
        
- **Practical Application:** This node is essential for incorporating existing models into a procedural setup. It can be used to reference a custom-modeled object to be used as an instance for scattering, or to import a curve object to use as a path for another mesh to follow. It also allows procedural effects to react to the position and rotation of a control object.