- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3
    
- **Core Function:** Provides the absolute file path to a key folder within the project's directory structure.
    
- **Key Properties & Settings:**
    
    - **Input (Name):** A string to specify which folder path is needed (e.g., "Data" might refer to the main game data directory).
        
    - **Output (Path):** A string containing the full, absolute path to the requested folder.
        
- **Practical Application:** A crucial utility for building robust, portable projects. Instead of hard-coding file paths like C:/Users/..., you use this node to reliably get the path to the save game folder or the assets folder, ensuring your game can find its files no matter where it's installed.