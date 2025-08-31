- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3
    
- **Core Function:** A utility node that safely combines multiple path components into a single, correctly formatted file path.
    
- **Key Properties & Settings:**
    
    - **Input (Path Sockets):** Multiple string inputs for the different parts of the path (e.g., a folder path and a file name). The "Add Socket" button allows for adding more components.
        
    - **Output (Path):** A single string containing the combined, properly formatted path (e.g., it will correctly add slashes / between components).
        
- **Practical Application:** The standard way to construct file paths for saving and loading. You would take the output from Get Master Folder and feed it into the first socket, then provide the save file name (e.g., save_slot_1.dat) in the second socket. This node ensures the resulting path is always correct, avoiding common errors.