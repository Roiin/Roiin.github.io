- **Editor:** Logic Node Editor
    
- **Node Group:** Game
    
- **Core Function:** Loads a game state that was previously saved using the Save Game node. This will restore all saved properties, object states, and scene information.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** A Boolean input that triggers the loading process when True.
        
    - **File Path/Saves (Socket):** A string input specifying the name of the save file to load.
        
    - **Slot (Socket):** An integer input specifying the particular save slot within the file to load, allowing for multiple save games.
        
    - **Done (Socket):** A flow control output that sends a pulse after the load command has been executed.
        
- **Practical Application:** Used in the main menu. When a player selects a save slot from a list and clicks "Load," the corresponding File Path/Saves and Slot information is fed to this node and its Condition is set to True.