- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Instantly sets an object's rotation relative to its parent's orientation, using a 3x3 orientation matrix.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The target object to rotate.
        
    - **Local Orientation (Socket):** A 3x3 matrix input for the new rotation relative to the parent.
        
    - **XYZ Checkboxes:** Selectively apply rotation to specific axes.
        
    - **Value (Socket):** Alternative name for the Local Orientation socket.
        
- **Practical Application:** Used to control the orientation of child objects within a hierarchy. For example, making a security camera (child) swivel back and forth on its mounting bracket (parent), independently of how the bracket itself is oriented in the world.