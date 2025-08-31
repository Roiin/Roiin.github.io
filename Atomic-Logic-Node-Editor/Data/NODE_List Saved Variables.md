- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3 - Variables
    
- **Core Function:** Reads a save file and outputs a list containing the names (keys) of all the variables stored within it.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Path):** The directory path of the file.
        
    - **Input (File):** The name of the file to read.
        
    - **Setting (Print):** A checkbox for debugging, likely prints the list to the console.
        
    - **Output (List):** A list of strings, where each string is the name of a saved variable.
        
    - **Output (Done):** A flow control pulse that activates after the list has been generated.
        
- **Practical Application:** Useful for debugging save files or for creating dynamic save/load menus that can show what data is present in a given save slot.