- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 2 - Character
    
- **Core Function:** Sets the maximum number of times a character can jump before needing to touch the ground again.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The character to modify.
        
    - **Input (Max Jumps):** An integer for the new maximum number of jumps (e.g., 2 for a double jump).
        
    - **Output (Done):** A flow control pulse that activates after the value is set.
        
- **Practical Application:** The core mechanic for implementing a double jump or multi-jump ability. This is often set once at the start or can be dynamically changed by a power-up.