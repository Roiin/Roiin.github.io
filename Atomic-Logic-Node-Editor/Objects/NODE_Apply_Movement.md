- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Applies a continuous translational force to an object, causing it to move. This is distinct from Set Position, which teleports. Apply Movement is used for smooth, frame-by-frame motion.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Local (Checkbox):** If checked, the Movement vector is interpreted in the object's local space (e.g., Y is always "forward"). If unchecked, it's in world space.
        
    - **Condition (Socket):** A Boolean input; movement is only applied on frames where this is True.
        
    - **Object (Socket):** The target object to move.
        
    - **Vector (Socket):** A 3D vector representing the direction and magnitude (speed) of the movement to be applied.
        
- **Practical Application:** The fundamental node for character and object movement. Typically used in an On Update loop, where an input vector (from Gamepad Sticks or keyboard logic) is fed into the Vector socket to move the player character.