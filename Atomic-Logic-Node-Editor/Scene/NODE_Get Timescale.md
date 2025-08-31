- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 4
    
- **Core Function:** Retrieves the current speed of the game's overall simulation (logic and physics).
    
- **Key Properties & Settings:**
    
    - **Output (Timescale):** A float value representing the current simulation speed (1.0 is normal speed).
        
- **Practical Application:** Useful for checking the game's state. For example, a UI element could use this to display an icon when the game is in slow-motion (timescale < 1.0).