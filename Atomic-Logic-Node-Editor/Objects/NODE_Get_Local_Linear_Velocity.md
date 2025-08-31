- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Get Attribute
    
- **Core Function:** Retrieves the speed and direction of an object's movement relative to its own local axes.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The target dynamic object.
        
    - **Local Linear Velocity (Socket):** A 3D vector output.
        
- **Practical Application:** Very useful for character controllers. It allows you to easily determine if the character is moving forward (positive Y value), backward (negative Y), or strafing (X values), regardless of which direction they are facing in the world.