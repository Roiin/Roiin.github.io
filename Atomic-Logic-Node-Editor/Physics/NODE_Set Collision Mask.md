- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 3
    
- **Core Function:** Dynamically changes an object's collision mask. The mask is a bitmask that determines which collision groups this object can interact with.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The object whose mask will be changed.
        
    - **Input (Bitmask):** The new integer bitmask value.
        
    - **Output (Done):** A flow control pulse that activates after the mask is set.
        
- **Practical Application:** Changing an object's collision properties at runtime. For example, activating a "Ghost" power-up by setting the player's mask so it no longer collides with the "Walls" group.