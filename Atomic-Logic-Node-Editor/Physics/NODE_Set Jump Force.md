- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 2 - Character
    
- **Core Function:** Sets the force applied when the character jumps. This is separate from the Jump action itself.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The character whose jump force will be modified.
        
    - **Input (Force):** A float value representing the new jump force.
        
    - **Output (Done):** A flow control pulse that activates after the force is set.
        
- **Practical Application:** Used for power-ups or special abilities. For example, a "Super Jump" power-up could temporarily increase the character's jump force.