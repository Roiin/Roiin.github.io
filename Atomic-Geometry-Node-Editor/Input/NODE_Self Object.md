- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Outputs a reference to the very object that the Geometry Nodes modifier is currently attached to and evaluating. This is crucial for making a procedural setup aware of its own world-space transform. Note: You cannot use this node to get the object's own geometry via an Object Info node, as this would create a circular dependency.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Self Object (Socket - Output):** A reference to the object that the modifier is currently on.
        
- **Practical Application:** This is essential for creating effects that are dependent on the object's world orientation, not its local geometry. For example, to procedurally add snow only to the upward-facing surfaces of a rock, regardless of how the rock is rotated. You would use the Self Object node, feed it into an Object Info node to get its world Rotation, and then use that rotation to transform the mesh's normals into world space. By comparing these world-space normals to a pure up-vector (0,0,1), you can create a mask that correctly identifies the "top" of the rock in the scene, ensuring snow always lands on top, even if you turn the rock upside down.