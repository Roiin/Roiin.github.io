- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each edge in a mesh, this node outputs the indices and positions of the two vertices that define it.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Vertex 1 / Vertex 2 (Sockets - Output):** The indices of the two vertices that form the edge.
        
    - **Position 1 / Position 2 (Sockets - Output):** The world-space positions of the two vertices. (Note: The ordering of Vertex 1 vs. Vertex 2 is not guaranteed to be consistent).
        
- **Practical Application:** This node is perfect for creating structures that are defined by the edges of a mesh, like a fence with posts and rails.
    
    1. Start with a simple Grid mesh to lay out your fence plan.
        
    2. **The Goal:** You want to instance fence posts on every vertex and place horizontal rails along every edge.
        
    3. **Posts:** You can instance posts directly on the grid's vertices using Instance on Points.
        
    4. **Rails:**
        
        - Use the Edge Vertices node. The Position 1 and Position 2 outputs give you the start and end points for each rail.
            
        - You can calculate the length of each rail by finding the Distance between Position 1 and Position 2.
            
        - You can find the center of each rail by taking the average of Position 1 and Position 2.
            
        - You can find the direction of each rail by subtracting Position 1 from Position 2.
            
        - Now, you can instance a "rail" object (a long cylinder) at the center of each edge. Use the calculated length to set its scale on one axis and the calculated direction to set its rotation (using an Align Euler to Vector node).
            
    5. The result is a complete, procedurally generated fence. The Edge Vertices node was the key to deconstructing the grid's edges into the start and end points needed to correctly place and orient the horizontal rails.