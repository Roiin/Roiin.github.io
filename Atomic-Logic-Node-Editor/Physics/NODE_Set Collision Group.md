- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 3
    
- **Core Function:** Dynamically changes an object's collision group. The group defines "what this object is" for collision purposes.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The object whose group will be changed.
        
    - **Input (Bitmask):** The new integer bitmask for the group.
        
    - **Output (Done):** A flow control pulse that activates after the group is set.
        
- **Practical Application:** Changing an object's "team" or type. For example, a character who is mind-controlled could have their collision group changed from "Player" to "Enemy" so that player-fired projectiles will now hit them.