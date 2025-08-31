- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Sets or creates a Game Property on a specified object and assigns it a value.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Object (Socket):** The object on which to set the property.
        
    - **Game Property (Socket):** A string input for the name of the property.
        
    - **Value (Socket):** The data to be assigned to the property.
        
- **Practical Application:** The primary method for changing an object's state. Used to decrease a player's "health" property after taking damage or to change an AI's "state" property from 'patrol' to 'attack'.