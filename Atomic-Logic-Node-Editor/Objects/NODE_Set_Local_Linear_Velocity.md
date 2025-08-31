- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Sets the linear velocity (speed and direction of movement) for a dynamic physics object, relative to its own local axes.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A Boolean input.
        
    - **Object (Socket):** The target physics object.
        
    - **Local Linear Velocity (Socket):** A 3D vector input for the new velocity. A vector of (0, 5, 0) will always propel the object forward along its own local Y-axis, regardless of its world orientation.
        
    - **XYZ Checkboxes:** Selectively apply velocity to specific local axes.
        
    - **Value (Socket):** Alternative name for the Local Linear Velocity socket.
        
- **Practical Application:** The standard method for character and vehicle movement. Applying a constant positive Y-velocity moves the character "forward" from their perspective. This is far more intuitive than calculating the world-space velocity vector every time the character turns.