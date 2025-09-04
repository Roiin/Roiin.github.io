- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For a given edge, this node finds its neighboring face corners, sorts them based on a weight, and then outputs the index of a single corner from that sorted list. It's a tool for querying the corners that are directly adjacent to an edge.
    
- **Key Properties & Settings:**
    
    - **Edge Index (Socket - Input):** The index of the edge to be queried.
        
    - **Weights (Socket - Input):** A field evaluated on the Face Corner domain. This is used to sort the neighboring corners. A common weight is the corner's index or its Z position.
        
    - **Sort Index (Socket - Input):** An integer that picks a corner from the sorted list (0 is the first, 1 is the second, etc.).
        
    - **Corner Index (Socket - Output):** The primary output; the global index of the selected face corner.
        
    - **Total (Socket - Output):** The number of faces connected to the edge (which is also the number of corners the node will find and sort).
        
- **Practical Application:** This node is for very specific topological selections. Imagine you have a mesh of an animal's wing, which is a thin, two-sided membrane. You want to procedurally draw a vein pattern that starts at the "front" edge of the wing.
    
    1. First, select the leading edge of the wing.
        
    2. **The Goal:** For each edge on this leading edge, you want to find the face corner that is on the "top" surface of the wing.
        
    3. Use the Corners of Edge node. The Edge Index is the index of each edge on the wing's leading edge.
        
    4. You need to sort the two adjacent corners (one on the top face, one on the bottom) by their Z-position to determine which is higher.
        
        - To do this, use a Separate XYZ node on the Position node and connect the Z output to the Weights input.
            
    5. The corner with the lower Z value will have a lower weight. To select the top corner (higher Z), you need the corner with the higher weight. Since there are only two corners (Total = 2), the one with the higher weight will have a Sort Index of 1. So, you set the Sort Index input to 1.
        
    6. The Corner Index output is now a list of the indices of all the face corners that lie on the top surface along the leading edge of the wing. You can now use this selection with a Sample Index to get their exact positions and use them as starting points for a procedural vein system that grows across the top of the wing membrane.