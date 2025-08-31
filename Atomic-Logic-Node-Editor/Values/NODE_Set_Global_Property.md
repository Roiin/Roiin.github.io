- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Sets or creates a global property and assigns it a value. This property can then be accessed by any Get Global Property node anywhere in the game.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Property (Socket):** A string input for the name of the global property.
        
    - **Value (Socket):** The data to be assigned to the property.
        
- **Practical Application:** Used to change game-wide states. A pause menu sets a "GameIsPaused" Boolean to True, which can then be checked by enemy AI logic trees to halt their behavior.