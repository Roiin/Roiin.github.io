- **Editor:** Logic Node Editor
    
- **Node Group:** Values
    
- **Core Function:** Provides a vector value, which is a container for multiple float numbers, typically used to represent positions, rotations, scales, or colors.
    
- **Key Properties & Settings:**
    
    - **Mode (Dropdown):** Selects the type and dimension of the vector.
        
        - 2D Vector: Contains X and Y components.
            
        - 3D Vector: Contains X, Y, and Z components.
            
        - 4D Vector: Contains X, Y, Z, and W components.
            
    - **Value Fields:** Numerical input fields for each component of the vector (e.g., X, Y for a 2D vector).
        
    - **Vector (Socket):** The vector data output.
        
- **Practical Application:** Crucial for any 3D math. A 2D Vector is used for screen coordinates. A 3D Vector is fundamental for setting object positions (Set World Position), defining movement direction (Apply Movement), or representing RGB colors. A 4D Vector can represent RGBA colors (including an alpha/transparency channel).