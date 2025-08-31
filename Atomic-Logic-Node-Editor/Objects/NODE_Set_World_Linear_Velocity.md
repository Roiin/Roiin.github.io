- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Sets the linear velocity (speed and direction of movement) for a dynamic physics object in world space.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A Boolean input.
        
    - **Object (Socket):** The target physics object.
        
    - **World Linear Velocity (Socket):** A 3D vector input for the new velocity.
        
    - **XYZ Checkboxes:** Selectively apply velocity to specific axes.
        
    - **Value (Socket):** Alternative name for the World Linear Velocity socket.
        
- **Practical Application:** Directly controlling the motion of physics objects. For example, setting the velocity of a thrown grenade or bringing a moving object to a complete stop by setting its velocity to (0, 0, 0).