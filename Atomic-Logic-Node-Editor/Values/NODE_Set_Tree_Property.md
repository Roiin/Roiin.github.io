- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Sets the value of a property that is local to the current Logic Tree. This is useful for storing temporary states or variables within a single tree without affecting the object's main properties.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A Boolean input; the node only executes if this is True.
        
    - **Object (Socket):** The object that owns the logic tree (often left unconnected to default to Self).
        
    - **Property (Socket):** A string input for the name of the tree property.
        
    - **Value (Socket):** The data (any type) to be assigned to the property.
        
- **Practical Application:** Managing internal states of a complex mechanic. For instance, in a combo attack system, a tree property "ComboStep" could be incremented and tracked entirely within the combat logic tree.