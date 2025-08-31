- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Compares the value of an object's Game Property to a given value and outputs a boolean result.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The target object.
        
    - **Property (Socket):** String input for the property name.
        
    - **Equal (Dropdown):** The comparison operator (e.g., Equal, Not Equal, Greater Than, Less Than).
        
    - **Value (Socket):** The value to compare against.
        
    - **If True (Socket):** The boolean output of the comparison.
        
- **Practical Application:** A more direct way to create conditions than using Get Object Property and a Compare node. Example: "Is player 'ammo' property Greater Than 0?" -> If True, allow the player to shoot.