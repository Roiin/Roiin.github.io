- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Sets the "Object Color" property of an object.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The target object.
        
    - **Color (Socket):** A 4D vector input for the new RGBA color.
        
- **Practical Application:** Used to change an object's color property, which can then be used by its material via the "Object Info" shader node. This allows for effects like flashing a character red when they take damage or changing their color to indicate their team or status.