- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Instantly sets an object's position relative to its parent's origin. If the object has no parent, this node behaves identically to Set World Position.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A Boolean input; the node only executes if this is True.
        
    - **Object (Socket):** The target object to move.
        
    - **Local Position (Socket):** A 3D vector input for the destination X, Y, and Z coordinates relative to the parent. A value of (0, 0, 0) will place the object's origin exactly at its parent's origin.
        
    - **XYZ Checkboxes:** Allows you to selectively apply the position change to only the X, Y, or Z axis.
        
    - **Value (Socket):** Alternative name for the Local Position socket.
        
- **Practical Application:** Essential for controlling the parts of a compound object. For example, positioning a cannon on a swivel base, where the cannon's position is always calculated relative to the base, not the entire world. It ensures that even if the parent (the base) moves, the child (the cannon) maintains its correct local offset.