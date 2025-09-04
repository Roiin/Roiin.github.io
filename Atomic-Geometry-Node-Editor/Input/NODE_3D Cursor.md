- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Provides the real-time world-space position and orientation of the scene's 3D Cursor. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Location (Socket - Output):** A vector representing the world-space position of the 3D Cursor.
        
    - **Rotation (Socket - Output):** The orientation of the 3D Cursor, provided as a standard rotation value.
        
- **Practical Application:** Imagine building a custom "Quick Place" tool for rapidly populating a scene. In the tool's Geometry Node graph, you would use this node to control where a new object is instanced. The Location and Rotation outputs would be plugged into a Transform Geometry node. The user workflow would be: 1. Place the 3D cursor precisely where an object should go. 2. Run your custom tool. The tool then reads the cursor's transform and instantly places an instance at that exact spot with the correct orientation.