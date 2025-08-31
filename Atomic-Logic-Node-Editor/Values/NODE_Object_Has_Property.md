- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Checks if a specified object has a Game Property with a given name. Outputs a Boolean value.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The object to check.
        
    - **Game Property (Socket):** A string input for the name of the property to look for.
        
    - **If True (Socket):** A Boolean output that is True if the property exists, and False otherwise.
        
- **Practical Application:** Useful for safely checking if an object is of a certain type before trying to access its properties, preventing errors. For example, "Does this object I collided with have a 'health' property? If yes, apply damage."