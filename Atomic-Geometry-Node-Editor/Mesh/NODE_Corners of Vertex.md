- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For a given vertex, this node finds all the face corners that meet at that vertex, sorts them based on a weight, and then outputs the index of a single corner from that sorted list. It's a tool for isolating one of the "slices" of a vertex's "pie".
    
- **Key Properties & Settings:**
    
    - **Vertex Index (Socket - Input):** The index of the vertex to be queried.
        
    - **Weights (Socket - Input):** A field evaluated on the Face Corner domain, used to sort the corners surrounding the vertex.
        
    - **Sort Index (Socket - Input):** An integer that picks a corner from the sorted list.
        
    - **Corner Index (Socket - Output):** The primary output; the global index of the selected face corner.
        
    - **Total (Socket - Output):** The number of corners (and thus, faces) that meet at the queried vertex.
        
- **Practical Application:** This node is essential for creating procedural selections that "radiate" out from a vertex. Imagine you have a mesh representing an animal's hide, and you want to select one single face adjacent to each vertex, always picking the face that is pointing most "upwards".
    
    1. **The Goal:** To create a sparse but consistent selection of faces across the entire mesh.
        
    2. Use the Corners of Vertex node. You need to sort the adjacent corners based on the direction their face is pointing.
        
    3. For the Weights, you can use the Normal of each face (interpolated to the corners). To sort by "upwards," you want the face normal with the highest Z-component. So, you can use the Z component of the Normal node as the weight.
        
    4. To pick the corner with the highest weight (the most upward-pointing), you need to know the Total number of corners at each vertex. You can then set the Sort Index to Total - 1 to pick the last item in the sorted list (the one with the highest Z-normal).
        
    5. The Corner Index output now gives you the index of one specific corner at each vertex. You can then use the Face of Corner node to find the index of the face that this corner belongs to.
        
    6. The result is a selection of faces, with one face selected at each vertex, and that face is always the one that is most oriented towards the sky. This could be used as a mask for placing dust or snow.