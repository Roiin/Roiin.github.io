- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Applies a rotational force (torque) to a dynamic physics object, causing it to accelerate its spin.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Local (Checkbox):** Toggles between local and world space for the torque axis.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The target physics object.
        
    - **Vector (Socket):** A 3D vector representing the torque to be applied around each axis.
        
- **Practical Application:** Used for physics-based rotation. For example, applying torque to the wheels of a vehicle to make them spin and propel the vehicle forward, or making a ragdoll character tumble realistically when hit.