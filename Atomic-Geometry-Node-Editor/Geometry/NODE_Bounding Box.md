- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Calculates the smallest possible cube-shaped volume (the bounding box) that fully encloses an input geometry. It outputs this bounding box as a new mesh and also provides the corner coordinates (Min and Max) of this box as vector values. Note: For instanced geometry, it calculates a bounding box for each individual instance; to get a single box for the entire collection, first use a Realize Instances node.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry to be measured.
        
    - **Bounding Box (Socket - Output):** The resulting cube mesh that encloses the input geometry.
        
    - **Min (Socket - Output):** A vector representing the corner of the box with the lowest X, Y, and Z coordinates.
        
    - **Max (Socket - Output):** A vector representing the corner of the box with the highest X, Y, and Z coordinates.
        
- **Practical Application:** This node is perfect for automatically placing objects of varying shapes and sizes flat on a surface, like populating a scene with a library of different animal models.
    
    - **The Problem:** When you instance an animal model whose origin is at its center, it will be placed half-buried in the ground.
        
    - **The Solution:**
        
        1. Use the Bounding Box node on the animal geometry before it is instanced.
            
        2. Take the Min output vector. Its Z component gives you the lowest point of the animal relative to its origin (this will be a negative number, e.g., -0.8 for a standing animal).
            
        3. Isolate this Z value using a Separate XYZ node.
            
        4. Negate it using a Math node (Multiply by -1). The result is now a positive offset (e.g., +0.8).
            
        5. Use a Combine XYZ node to create a new vector (0, 0, 0.8).
            
        6. When you instance the animal onto your ground plane, add this vector to its position. This effectively lifts each animal up by the exact amount needed so that its lowest point rests perfectly on the ground, regardless of its unique shape or size.