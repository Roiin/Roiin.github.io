- **Editor:** Logic Node Editor
    
- **Node Group:** Lights
    
- **Core Function:** Enables or disables shadow casting for a specified Light object at runtime.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control output.
        
    - **Condition (Socket):** A boolean input.
        
    - **Light Object (Socket):** The target Light object.
        
    - **Use Shadow (Checkbox):** If checked, enables shadows for this light. If unchecked, disables them.
        
- **Practical Application:** Primarily used for performance optimization. You can disable shadows for lights that are far from the player or are not critically important to the scene's visual fidelity, then re-enable them as the player gets closer.