- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Transforms a mesh into its "dual" representation. This means each face from the original mesh becomes a single vertex in the new mesh, and each original vertex becomes a face. This is a powerful way to generate complex geometric patterns. **Warning: This node works best on manifold (watertight) geometry.**
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be converted.
        
    - **Keep Boundaries (Socket - Input):** A boolean. If True, it preserves the open edges of the original mesh instead of creating large, stretched faces.
        
    - **Dual Mesh (Socket - Output):** The resulting dual mesh. Attributes from the face domain of the original mesh are transferred to the point domain of the new mesh.
        
- **Practical Application:** This node is famous for its ability to turn a simple triangulated mesh into complex hexagonal and pentagonal patterns, perfect for creating a soccer ball or sci-fi paneling.
    
    1. **The Goal:** To create the classic black and white panel pattern of a soccer ball.
        
    2. **The Start:** Begin with an Icosphere primitive. An icosphere is made entirely of uniform triangles.
        
    3. Apply the Dual Mesh node to the icosphere.
        
        - Every triangular face of the icosphere becomes a vertex.
            
        - Every vertex of the icosphere (where 5 or 6 triangles met) becomes a pentagonal or hexagonal face.
            
    4. The output of the Dual Mesh node is now a perfect "truncated icosahedron"—the exact geometric shape of a soccer ball.
        
    5. To color the panels, you can use the Face Neighbors node. The pentagons will have a Vertex Count of 5, and the hexagons will have a Vertex Count of 6. You can use this to create a selection for the pentagons and assign them a black material, while the hexagons get a white material.
        
    6. This same technique can be used with any triangulated mesh to create complex, organic-looking paneling for sci-fi armor or architecture.