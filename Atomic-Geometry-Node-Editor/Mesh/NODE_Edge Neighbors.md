- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each edge in a mesh, this node provides information about its neighboring faces. Its primary use is to identify the boundary edges of a mesh island.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Face Count (Socket - Output):** An integer representing the number of faces connected to the edge.
        
        - A value of 2 indicates a normal, interior edge.
            
        - A value of 1 indicates a "boundary" edge—an edge on the open perimeter of a mesh, like the rim of a hole.
            
        - A value of 0 indicates a "loose" edge that is not part of any face.
            
- **Practical Application:** This node is perfect for procedurally adding a thickened border or frame to an object with holes, like creating a metal rim around the eye sockets of an animal's skull.
    
    1. Start with a skull mesh that has open holes for the eyes and nose.
        
    2. **The Goal:** You want to procedurally create a separate, thick metal ring that perfectly traces the outline of these holes.
        
    3. Use the Edge Neighbors node. The Face Count output will be 1 for all the edges that form the rim of the eye sockets.
        
    4. Use a Compare node to create a Boolean selection where Face Count is equal to 1.
        
    5. Use a Separate Geometry node with this selection to isolate only the boundary edges into their own geometry stream.
        
    6. The output is a new geometry object containing only the curve outlines of the eye sockets.
        
    7. You can now use a Curve to Mesh node on these curves with a Curve Circle as the profile to create a solid, tube-like metal rim. Because it's procedural, if you were to change the shape of the eye sockets, the metal rim would automatically update to match the new boundary.