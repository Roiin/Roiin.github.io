- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Get Attribute
    
- **Core Function:** Retrieves the speed and direction of an object's movement through world space. This applies only to objects with physics enabled.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The target dynamic object.
        
    - **World Linear Velocity (Socket):** A 3D vector output. The direction of the vector is the direction of movement, and its magnitude is the speed.
        
- **Practical Application:** Used for physics-based logic. Examples: checking an object's speed to determine if it should play a "running" or "walking" animation, detecting if a falling object has stopped moving to trigger a "landed" event, or calculating impact force.