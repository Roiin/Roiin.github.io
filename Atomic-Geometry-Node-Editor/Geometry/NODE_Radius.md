- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Outputs the per-point radius attribute, which is a float value that typically controls the thickness of curves or the display size of points in a point cloud.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Radius (Socket - Output):** A float field representing the radius value for each point.
        
- **Practical Application:** Imagine you are procedurally creating a thorny vine wrapping around a pillar. The vine itself is a curve that has been given a tapering thickness (e.g., using a Set Radius node so it's thinner at the tip). To make the thorns look natural, they should be larger on the thicker parts of the vine and smaller on the thinner parts.
    
    1. First, you use Instance on Points to scatter thorn objects (like small cones) along the vine curve.
        
    2. To control their size, you connect the Radius node's output directly into the Scale input of the Instance on Points node.
        
    3. The result is that each thorn's scale is directly driven by the vine's thickness at that exact point. Thorns on the thick base of the vine will be large, while thorns near the thin tip will be tiny, creating a believable and organic-looking asset.