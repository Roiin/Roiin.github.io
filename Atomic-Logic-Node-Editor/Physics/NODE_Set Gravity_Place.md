- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 3
    
- **Core Function:** Sets the gravity acceleration vector for a specific physics object, overriding the scene's default gravity for that object.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Object):** The object to affect.
        
    - **Input (Gravity):** A 3D vector for the new gravity (e.g., (0, 0, -9.8) for standard gravity).
        
    - **Output (Done):** A flow control pulse that activates after the gravity is set.
        
- **Practical Application:** Creating localized physics zones, such as a zero-gravity room or a body of water with upward buoyant force.