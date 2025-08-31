- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Get Attribute
    
- **Core Function:** Retrieves the absolute rotation of a specified object within the game world's coordinate system, expressed as a 3x3 orientation matrix.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The target object to query.
        
    - **World Orientation (Socket):** A 3x3 matrix output.
        
- **Practical Application:** Used for advanced rotational calculations where Euler angles might be insufficient (e.g., to avoid gimbal lock). Often used to align one object's rotation precisely with another's.