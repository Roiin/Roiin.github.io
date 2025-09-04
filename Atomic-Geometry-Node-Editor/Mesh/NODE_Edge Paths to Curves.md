- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Reads the "direction map" output from a Shortest Edge Paths node and generates visible curve splines that trace these paths from a set of Start Vertices to their calculated endpoints.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh that the paths were calculated on.
        
    - **Start Vertices (Socket - Input):** A Boolean selection identifying the vertices where the curves should begin.
        
    - **Next Vertex Index (Socket - Input):** This is the critical input. It should be connected directly to the Next Vertex Index output of a Shortest Edge Paths node.
        
    - **Curves (Socket - Output):** The resulting curve geometry, with a separate spline for each traced path.
        
- **Practical Application:** This node is the key to visualizing the results of the Shortest Edge Paths calculation, perfect for creating a lightning effect that crawls across an animal's body.
    
    1. First, you set up a Shortest Edge Paths node on your animal mesh. The End Vertex is a single point on the creature's head (the target), and the Edge Cost is the length of each edge. This calculates the shortest path from everywhere on the body to the head.
        
    2. **The Goal:** You now want to draw the actual lightning bolts, starting from the animal's feet and hands and traveling up to its head.
        
    3. Use the Edge Paths to Curves node.
        
        - The Mesh is your animal mesh.
            
        - The Next Vertex Index is connected directly from the Shortest Edge Paths node.
            
        - For the Start Vertices, you create a selection of the vertices on the animal's hands and feet.
            
    4. **The Result:** The node will start at each selected foot/hand vertex and "walk" along the pre-calculated path, tracing it step-by-step until it reaches the head. The Curves output will be a set of splines that look like lightning bolts organically crawling up the creature's limbs and torso, perfectly conforming to the surface of the mesh. You can then give these curves a glowing, emissive material to complete the effect.