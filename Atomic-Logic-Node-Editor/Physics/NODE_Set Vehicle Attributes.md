- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 1 - Vehicle
    
- **Core Function:** Modifies the physical properties of an existing vehicle constraint at runtime.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the attribute change.
        
    - **Input (Vehicle, Collider, Wheels):** References to the vehicle components to be modified.
        
    - **Input (Suspension, Stiffness, Damping, Friction):** Float inputs that allow you to set new values for the vehicle's handling characteristics.
        
    - **Output (Done):** A flow control pulse that activates after the attributes have been changed.
        
- **Practical Application:** Used for dynamic vehicle tuning or status effects. For example, driving onto an ice patch could trigger this node to temporarily lower the vehicle's Friction, while a "nitro boost" power-up could increase its Power attribute.