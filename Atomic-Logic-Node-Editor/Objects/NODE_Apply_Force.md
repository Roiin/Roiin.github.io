- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Applies a force to a dynamic physics object, causing it to accelerate. This is used for physics-based movement that respects mass and inertia.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Local (Checkbox):** Toggles whether the force is applied in local or world space.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The target physics object.
        
    - **Vector (Socket):** A 3D vector representing the direction and magnitude of the force.
        
- **Practical Application:** Used for realistic physics interactions. Applying a force to a character for a jump, creating a rocket thruster effect, or simulating the impact of an explosion by applying a strong outward force to nearby objects.