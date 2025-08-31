- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Retrieves the value of a Game Property from a specified object.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The object from which to get the property.
        
    - **Game Property (Socket):** A string input for the name of the property to retrieve (e.g., "health", "ammo").
        
    - **Property Value (Socket):** The data output, providing the value of the requested property.
        
- **Practical Application:** The primary method for reading an object's state. Used to check a player's health before applying damage, get an AI's current state, or read the number of coins a player has collected.