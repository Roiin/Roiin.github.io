
- **Editor:** Logic Node Editor
    
- **Node Group:** Game
    
- **Core Function:** Restarts the game by reloading the currently active scene to its initial state. All objects and properties are reset to their default values.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** A Boolean input that triggers the restart when True.
        
    - **Done (Socket):** A flow control output that sends a pulse after the restart command has been issued.
        
- **Practical Application:** Essential for "Game Over" screens or pause menu options. When a player selects "Restart," this node is triggered, resetting the level.