- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 2 - Dict
    
- **Core Function:** The primary "read" operation. It looks up a key in a dictionary and returns the value associated with it. It includes a default value to prevent errors if the key is not found.
    
- **Key Properties & Settings:**
    
    - **Input (Dictionary):** The dictionary to read from.
        
    - **Input (Key):** The key whose value you want to retrieve.
        
    - **Input (Default Value):** The value that will be returned if the specified key does not exist in the dictionary.
        
    - **Output (Property Value):** The value found for the key, or the default value.
        
- **Practical Application:** This is how you retrieve data to make decisions. "Get the value for the key 'is_poisoned' from the character's status dictionary. If the value is true, apply damage." The Default Value is crucial for safe checks: "Get 'ammo_count'; if it doesn't exist, the default of 0 is returned."