- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 2 - Character
    
- **Core Function:** Retrieves various state information from a character physics object.
    
- **Key Properties & Settings:**
    
    - **Input (Object):** The character object to query.
        
    - **Output (Max Jumps, Current Jump Count):** Integers related to the character's multi-jump capability.
        
    - **Output (Gravity):** The current gravity force acting on the character.
        
    - **Output (Walk Direction):** The current direction of movement.
        
    - **Output (On Ground):** A critical boolean that is true only when the character is standing on a surface.
        
- **Practical Application:** Essential for state management in a character controller. The On Ground output is used to determine if the player is allowed to jump, and Walk Direction can be used for animation logic.