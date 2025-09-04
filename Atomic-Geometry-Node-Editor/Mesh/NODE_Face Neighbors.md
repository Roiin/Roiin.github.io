- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each face in a mesh, this node provides information about its own vertices and its neighboring faces.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Vertex Count (Socket - Output):** An integer representing the number of vertices (or sides) each face has. For a triangle, this is 3; for a quad, it is 4. This is the primary method for identifying N-gons.
        
    - **Neighboring Face Count (Socket - Output):** An integer representing the number of other faces that are connected to the current face by an edge.
        
- **Practical Application:** The Vertex Count output is an essential tool for mesh cleanup and for applying effects only to specific polygon types, like creating windows only on quad faces.
    
    1. Imagine you have a complex architectural model of a building that was imported from another program. The mesh is messy and contains a mix of triangles, quads, and N-gons (faces with more than 4 vertices).
        
    2. **The Goal:** You want to procedurally add a window frame to every face that is a perfect, four-sided quad, and ignore all the triangles and N-gons.
        
    3. Use the Face Neighbors node. The Vertex Count output will be 4 for all the quads.
        
    4. Use a Compare node to create a Boolean selection where Vertex Count is equal to 4.
        
    5. This selection now perfectly isolates every quad face on the mesh. You can feed this selection into a Scale Elements node to inset the faces, and then an Extrude Mesh node to create the window recesses.
        
    6. The result is that windows are correctly and robustly generated only on the suitable four-sided faces, while the unsuitable parts of the mesh are left untouched.