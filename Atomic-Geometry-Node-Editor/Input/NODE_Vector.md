- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Outputs a vector value composed of three separate numerical inputs (X, Y, and Z).
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **X, Y, Z (Properties):** Three numeric fields on the node to define the individual components of the vector.
        
    - **Vector (Socket - Output):** The combined X, Y, Z vector value.
        
- **Practical Application:** It's used to define a direction or dimension in 3D space. For example, to procedurally create a wooden plank from a default cube, you can connect a Vector node to the Scale input of a Transform Geometry node. By setting the vector's values to (X: 4.0, Y: 0.5, Z: 0.1), you can instantly stretch the cube into a long, flat, thin plank shape. This provides direct, numerical control over an object's proportions.