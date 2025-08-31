- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3 - Variables
    
- **Core Function:** Saves an entire dictionary object to a file, overwriting its previous contents. This is an efficient way to save a complete game state.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the save.
        
    - **Input (Path):** The directory path to save to.
        
    - **Input (File):** The name of the file to save to.
        
    - **Input (Variables):** The dictionary object containing all the data to be saved.
        
    - **Output (Done):** A flow control pulse that activates after the save is complete.
        
- **Practical Application:** The counterpart to Load Variable Dict. You would typically maintain the player's entire state (stats, inventory, quests) in a single master dictionary, and when the player saves, you use this node to write that entire dictionary to the save file in one operation.