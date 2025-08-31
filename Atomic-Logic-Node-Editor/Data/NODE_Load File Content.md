- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3
    
- **Core Function:** Reads the raw content of an external file (like a text file) and makes it available for use.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the file read operation.
        
    - **Output (Loaded, Updated, Status, Datatype, Item):** Similar to Load Scene, these outputs provide feedback on the loading process. The Item output would contain the actual file content (e.g., as a string).
        
- **Practical Application:** Used for loading data that isn't in UPBGE's native save format. Examples include loading dialogue from a .txt file, level layouts from a .json file, or configuration settings from an .ini file.