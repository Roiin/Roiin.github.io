- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Applies an instantaneous change in velocity (an impulse) to a dynamic physics object. It's like a sudden, powerful push.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the impulse.
        
    - **Local (Checkbox):** Toggles between local and world space for the impulse direction.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The target physics object.
        
    - **Vector (Socket):** A 3D vector for the direction and magnitude of the impulse.
        
- **Practical Application:** Perfect for single, impactful events. Used for the "kick" of a weapon firing, a character's jump (as an alternative to Apply Force), or launching an object from a catapult.