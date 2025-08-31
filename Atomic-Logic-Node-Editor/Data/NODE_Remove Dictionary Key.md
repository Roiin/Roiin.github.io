- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 2 - Dict
    
- **Core Function:** Finds a specified key in a dictionary and completely removes both the key and its associated value.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Dictionary):** The dictionary to modify.
        
    - **Input (Key):** The key of the entry to be removed.
        
    - **Output (Done):** A flow control pulse that activates after the entry is removed.
        
- **Practical Application:** Used to remove state that is no longer needed. For example, when a timed power-up expires, you remove the "has_speed_boost": true entry from the player's status dictionary.