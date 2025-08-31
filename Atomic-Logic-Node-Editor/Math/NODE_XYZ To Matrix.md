- **Editor:** Logic Node Editor
    
- **Node Group:** Math
    
- **Core Function:** Constructs a 3x3 transformation matrix from two input vectors (e.g., a "Forward" and "Up" vector).
    
- **Key Properties & Settings:**
    
    - **Input (Forward):** The vector representing the forward direction.
        
    - **Input (Up):** The vector representing the up direction.
        
    - **Output (Matrix):** The resulting 3x3 orientation matrix.
        
- **Practical Application:** Advanced operations for setting an object's orientation. For example, making a character always face their direction of movement by constructing a new orientation matrix from their velocity vector each frame.