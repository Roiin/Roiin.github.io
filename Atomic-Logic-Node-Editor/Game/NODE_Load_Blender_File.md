- **Editor:** Logic Node Editor
    
- **Node Group:** Game
    
- **Core Function:** Halts the current game instance and loads a different .blend file. This is a primary method for transitioning between distinct levels or large game worlds that are stored in separate files.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** A Boolean input. The node executes its function only on the logic tick where this input is True.
        
    - **File Name (Socket):** A string input for the path to the target .blend file. Using a // prefix (e.g., //levels/level_02.blend) makes the path relative to the currently running file.
        
- **Practical Application:** Used to create level transitions. A player object might collide with an "exit trigger," which sets a property to True. This property is fed into the Condition socket, loading the next level file specified in File Name.