- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For a given face, this node finds all of its corners, sorts them based on a weight, and then outputs the index of a single corner from that sorted list. It's a tool for isolating a specific corner of a face based on some criteria.
    
- **Key Properties & Settings:**
    
    - **Face Index (Socket - Input):** The index of the face to be queried.
        
    - **Weights (Socket - Input):** A field evaluated on the Face Corner domain. This is used to sort the corners of the face.
        
    - **Sort Index (Socket - Input):** An integer that picks a corner from the sorted list (0 is the one with the lowest weight, 1 is the second-lowest, etc.).
        
    - **Corner Index (Socket - Output):** The primary output; the global index of the selected face corner.
        
    - **Total (Socket - Output):** The number of corners the queried face has (e.g., 3 for a triangle, 4 for a quad).
        
- **Practical Application:** This node is perfect for creating orientation-aware effects, like placing a directional "arrow" texture on every face of a mesh, with the arrow always pointing towards the "lowest" corner of that face.
    
    1. Start with a complex, triangulated mesh, like the faceted shell of a tortoise.
        
    2. **The Goal:** You want to apply a texture to each triangular face, and you need to control the texture's rotation so that it's consistently aligned. A good way to do this is to align one axis of the texture with the edge leading from the lowest corner to the next.
        
    3. Use the Corners of Face node.
        
        - To find the "lowest" corner, you need to sort the corners by their Z-position. Connect the Z component of the Position node to the Weights input.
            
        - To select the corner with the lowest Z-position, set the Sort Index to 0.
            
        - The Corner Index output now gives you the index of the single lowest corner for every face.
            
    4. You can then use other topology nodes (like Offset Corner in Face) to find the next corner in the face loop.
        
    5. Now that you have the positions of the lowest corner and the next corner, you can calculate a direction vector between them. This vector can be used with an Align Euler to Vector node to create a consistent rotation for each face's UVs or for an instanced object.