- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 3
    
- **Core Function:** Toggles an object's "Rigid Body" physics state. A rigid body is affected by forces, gravity, and collisions.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Object):** The object to affect.
        
    - **Setting (Enabled):** If checked, sets the object to be a rigid body. If unchecked, it becomes static.
        
    - **Output (Done):** A flow control pulse that activates after the state is changed.
        
- **Practical Application:** Activating physics on demand. For example, a bridge that is initially static can be made into a collapsing rigid body after an explosion.