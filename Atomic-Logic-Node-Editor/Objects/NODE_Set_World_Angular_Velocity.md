- **Editor:** Logic Node Editor
    
- - **Node Group:** Objects > Set Attribute
        
- **Core Function:** Sets the angular velocity (speed and axis of rotation) for a dynamic physics object in world space.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A Boolean input.
        
    - **Object (Socket):** The target physics object.
        
    - **World Angular Velocity (Socket):** A 3D vector input for the new angular velocity.
        
    - **XYZ Checkboxes:** Selectively apply angular velocity to specific axes.
        
    - **Value (Socket):** Alternative name for the World Angular Velocity socket.
        
- **Practical Application:** Directly controlling the spin of physics objects, such as making a saw blade spin at a constant rate or stopping a tumbling object.