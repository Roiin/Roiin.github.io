- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Sets an object's entire transformation (position, rotation, and scale) at once using a 4x4 matrix, relative to its parent object.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The target object.
        
    - **Local Transform (Socket):** A 4x4 matrix input defining the new local transform.
        
    - **XYZ Checkboxes:** Selectively apply parts of the transform.
        
    - **Value (Socket):** Alternative name for the Local Transform socket.
        
- **Practical Application:** Used for complex hierarchical transformations where the object's entire local transform needs to be set or reset precisely, such as snapping the components of a modular weapon into their correct relative positions.