- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3 - Variables
    
- **Core Function:** Loads an entire file's contents into a single dictionary object. This is a highly efficient way to load a complete game state.
    
- **Key Properties & Settings:**
    
    - **Input (Path):** The directory path of the file.
        
    - **Input (File):** The name of the file to load.
        
    - **Output (Variables):** A dictionary containing all the key-value pairs from the file.
        
- **Practical Application:** A more advanced and efficient way to load a game. Instead of loading each variable one-by-one, you load the entire save file into a dictionary at once, then use Get Dictionary Key to retrieve the specific data you need.