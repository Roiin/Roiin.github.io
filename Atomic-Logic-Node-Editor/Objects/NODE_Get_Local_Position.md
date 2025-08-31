- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Get Attribute
    
- **Core Function:** Retrieves the position of an object's origin relative to its parent object. If the object has no parent, this is the same as its world position.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The target object.
        
    - **Local Position (Socket):** A 3D vector output.
        
- **Practical Application:** Used when working with parent-child hierarchies. For example, to check the position of a turret on a tank relative to the tank's body, not the entire world.