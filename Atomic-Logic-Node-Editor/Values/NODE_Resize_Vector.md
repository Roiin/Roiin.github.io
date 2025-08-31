- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Vector
    
- **Core Function:** Converts a vector of one dimension to another (e.g., 2D to 3D, or 3D to 2D).
    
- **Key Properties & Settings:**
    
    - **Mode (Dropdown):** Specifies the target vector dimension (e.g., 2D Vector).
        
    - **Vector (Socket Input):** The source vector to be converted.
        
    - **Vector (Socket Output):** The resulting resized vector.
        
- **Practical Application:** A utility node for managing data flow between systems that expect different vector types. For example, taking a 3D world position and converting it to a 2D vector for UI mapping (though World To Screen is often better for this).