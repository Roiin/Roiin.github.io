- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 2 - Character
    
- **Core Function:** Directly sets the linear velocity of a physics object, overriding any other forces.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Object):** The object whose velocity will be set.
        
    - **Input (Velocity):** A 3D vector representing the new velocity in X, Y, and Z directions.
        
    - **Input (Time):** A float that likely controls the duration for which this velocity is applied.
        
    - **Setting (Local):** If checked, the velocity is applied relative to the object's orientation.
        
    - **Output (Done):** A flow control pulse that activates after the velocity is set.
        
- **Practical Application:** Useful for non-standard movement like dashes, knockback from explosions, or setting the character's movement on a conveyor belt. It provides more direct, immediate control over movement than the Walk node.