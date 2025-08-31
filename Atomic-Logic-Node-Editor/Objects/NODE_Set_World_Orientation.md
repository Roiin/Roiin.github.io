- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Set Attribute
    
- **Core Function:** Instantly sets an object's rotation in the world's coordinate system using a 3x3 orientation matrix.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A Boolean input.
        
    - **Object (Socket):** The target object to rotate.
        
    - **World Orientation (Socket):** A 3x3 matrix input for the new rotation.
        
    - **XYZ Checkboxes:** Selectively apply rotation to specific axes.
        
    - **Value (Socket):** Alternative name for the World Orientation socket.
        
- **Practical Application:** Used for precise, non-incremental rotation. Can be used to make an object perfectly match the rotation of another by feeding the output of a Get World Orientation node into this one.