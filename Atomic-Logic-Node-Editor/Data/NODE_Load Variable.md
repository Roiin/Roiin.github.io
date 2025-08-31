- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3 - Variables
    
- **Core Function:** Reads a single, named variable from a specified file on disk.
    
- **Key Properties & Settings:**
    
    - **Input (Path):** The directory path where the file is located (e.g., //Data).
        
    - **Input (File):** The name of the file to read from (e.g., savegame.dat).
        
    - **Input (Name):** The name (key) of the specific variable to load.
        
    - **Input (Default Value):** The value that will be returned if the file or the variable within it does not exist.
        
    - **Output (Value):** The loaded value, or the default value.
        
- **Practical Application:** Loading a specific piece of player data when the game starts, such as player_health, current_level, or ammo_count from a save file.