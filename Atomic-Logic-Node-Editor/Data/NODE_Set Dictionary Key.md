- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 2 - Dict
    
- **Core Function:** The primary "write" operation for dictionaries. It adds a new key-value pair to a dictionary or, if the key already exists, it updates the value associated with that key.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Dictionary):** The target dictionary to modify.
        
    - **Input (Key):** The key to be added or updated.
        
    - **Input (Value):** The new value to be assigned to the key.
        
    - **Output (Done):** A flow control pulse that activates after the operation is complete.
        
- **Practical Application:** This is how you store and modify state. Examples: player_stats["health"] = 85, quest_log["main_quest"] = "completed". This is the fundamental node for changing data in a dictionary.