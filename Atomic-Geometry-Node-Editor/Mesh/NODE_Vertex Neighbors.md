- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each vertex in a mesh, this node outputs the number of edges and faces that are connected to it, providing a measure of its local connectivity (its "valence").
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Vertex Count (Socket - Output):** An integer representing the number of other vertices connected to this vertex by an edge.
        
    - **Face Count (Socket - Output):** An integer representing the number of faces that share this vertex.
        
- **Practical Application:** This node is perfect for procedurally identifying and selecting the corners of a mesh, for example, to place support pillars on a building's floor plan.
    
    1. Start with a Grid primitive to represent the rectangular floor plan of a building.
        
    2. **The Goal:** You want to instance a pillar model on each of the four outer corners, and nowhere else.
        
    3. **The Problem:** You need a procedural way to select only the four corner vertices, regardless of the grid's resolution.
        
    4. **The Solution:**
        
        - Use the Vertex Neighbors node. The Vertex Count output gives you the number of edges connected to each vertex.
            
        - For a standard grid, the four corner vertices are the only ones connected to exactly **2** edges. The vertices along the sides are connected to 3, and the interior vertices are connected to 4.
            
        - Use a Compare node to create a Boolean selection where Vertex Count is equal to 2.
            
        - This selection is now True for only the four corner vertices.
            
    5. Feed this selection into the Selection input of an Instance on Points node. The result is that your pillar models are placed perfectly and exclusively on the corners of your floor plan. If you change the size or resolution of the grid, the corners are still correctly identified, and the pillars will update their positions automatically.