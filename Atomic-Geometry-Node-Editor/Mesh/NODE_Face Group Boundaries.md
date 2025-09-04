- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For a mesh where faces have been grouped with an integer ID, this node finds and outputs a Boolean selection of all the edges that form the boundaries between these groups.
    
- **Key Properties & Settings:**
    
    - **Face Group ID (Socket - Input):** An integer field on the Face domain. The node will identify the edges separating faces with different ID values.
        
    - **Boundary Edges (Socket - Output):** A Boolean field on the Edge domain. It is True for any edge that is shared by two faces with different Group IDs.
        
- **Practical Application:** This node is fundamental for procedural UV unwrapping and for creating geometric details along seams, like the grout between bathroom tiles.
    
    1. First, create a Grid mesh for your bathroom wall.
        
    2. Use a Voronoi Texture set to 'Cells' to generate a tile pattern. Convert its Color output (which gives a random color to each cell) into a unique Face Group ID for each tile.
        
    3. **The Goal:** You want to create a 3D grout line in the cracks between the tiles.
        
    4. Feed your procedural Face Group ID into the Face Group Boundaries node. The Boundary Edges output is now a perfect selection of all the edges between the tiles.
        
    5. Use a Separate Geometry node to isolate these boundary edges. The output is now a curve-like mesh representing the grout lines.
        
    6. You can then use Extrude Mesh on this separated geometry (extruding the edges downwards) and a Bevel modifier to create a realistic, inset grout effect. The Face Group Boundaries node was the key step that allowed you to procedurally "find" the cracks between your procedurally generated tiles.