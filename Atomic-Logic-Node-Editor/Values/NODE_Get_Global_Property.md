- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Retrieves the value of a global property. Global properties are not tied to any specific object and are accessible from any logic tree in the entire game instance.
    
- **Key Properties & Settings:**
    
    - **Property (Socket):** A string input for the name of the global property to retrieve.
        
    - **Default Value (Socket):** The value to output if the requested global property does not exist.
        
    - **Value (Socket):** The data output, providing the value of the requested property or the default value.
        
- **Practical Application:** Ideal for managing game-wide states, such as "Game Is Paused," "Current Difficulty Level," or tracking progress across multiple scenes (e.g., "Total Golden Skulls Found").