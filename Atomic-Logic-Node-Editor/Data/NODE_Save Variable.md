- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3 - Variables
    
- **Core Function:** Saves a single variable under a specific name to a file on disk. If the file doesn't exist, it is created.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the save operation.
        
    - **Input (Path):** The directory path to save to.
        
    - **Input (File):** The name of the file to save to.
        
    - **Input (Name):** The name (key) to assign to the variable being saved.
        
    - **Input (Value):** The actual data to be saved.
        
    - **Output (Done):** A flow control pulse that activates after the save is complete.
        
- **Practical Application:** The core of a save system. Used when the player hits a save point to write their current status (health, position, inventory items) to a file, one variable at a time.