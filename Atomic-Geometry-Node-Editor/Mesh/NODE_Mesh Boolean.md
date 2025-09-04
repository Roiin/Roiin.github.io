- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Performs Boolean operations (Intersect, Union, Difference) between two meshes, allowing for complex cutting, subtraction, and merging of geometry. This is the procedural equivalent of the Boolean modifier.
    
- **Key Properties & Settings:**
    
    - **Mesh 1 / Mesh 2 (Sockets - Input):** The two input meshes for the operation. The order matters for the 'Difference' operation.
        
    - **Operation (Property):** The core control for the node:
        
        - **Intersect:** The output mesh is only the volume that was shared by both input meshes.
            
        - **Union:** The two meshes are merged into a single, watertight volume, with any interior geometry removed.
            
        - **Difference:** The volume of Mesh 2 is subtracted from Mesh 1.
            
    - **Solver (Property):** The algorithm to use. 'Exact' is slower but more robust, especially for overlapping geometry, while 'Float' is faster but less reliable.
        
    - **Mesh (Socket - Output):** The resulting mesh geometry from the Boolean operation.
        
    - **Intersecting Edges (Socket - Output):** (Exact Solver only) A Boolean edge selection that is True for the new edges created where the two meshes intersected.
        
- **Practical Application:** The 'Difference' operation is perfect for procedurally carving details into a surface, like creating eye sockets in a creature's head.
    
    1. Start with a base mesh for your animal's head (e.g., a subdivided UV Sphere). This will be Mesh 1.
        
    2. Create two smaller spheres to represent the volume of the eyes. Position them so they intersect the head where the eye sockets should be. Join Geometry them into a single data stream. This will be Mesh 2.
        
    3. **The Goal:** You want to cut perfect, spherical holes into the head mesh.
        
    4. Use the Mesh Boolean node. Set the Operation to 'Difference'.
        
    5. The result is that the volume of the two smaller eye spheres is subtracted from the head, leaving behind two perfectly clean, concave eye sockets.
        
    6. The Intersecting Edges output is also very useful. You can use this selection to procedurally Bevel the rim of the new eye sockets, giving them a softer, more organic transition into the rest of the face.