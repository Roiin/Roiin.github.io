- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Sets an object's entire transformation (position, rotation, and scale) at once using a 4x4 matrix.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A Boolean input.
        
    - **Object (Socket):** The target object.
        
    - **World Transform (Socket):** A 4x4 matrix input.
        
    - **XYZ Checkboxes:** Selectively apply parts of the transform.
        
    - **Value (Socket):** Alternative name for the World Transform socket.
        
- **Practical Application:** The most complete way to synchronize two objects. You can get the transform from a "master" object and apply it to a "slave" object every frame to make them move and rotate in perfect unison.