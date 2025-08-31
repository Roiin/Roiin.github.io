- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Instantly teleports an object to a specified position in the world's coordinate system.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Object (Socket):** The target object to move.
        
    - **World Position (Socket):** A 3D vector input for the destination X, Y, and Z coordinates.
        
    - **XYZ Checkboxes:** Allows you to selectively apply the position change to only the X, Y, or Z axis.
        
    - **Value (Socket):** Alternative name for the World Position socket.
        
- **Practical Application:** Used for teleportation, spawning objects at a specific location, or resetting an object's position. For example, when a player falls out of the world, this node is used to move them back to the last checkpoint.