- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each face in a mesh, this node outputs a float value representing its surface area.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Area (Socket - Output):** A float field on the Face domain, where each value is the area of the corresponding face.
        
- **Practical Application:** This node is perfect for controlling the density of scattered elements based on the size of the underlying faces, for example, when placing windows on a skyscraper.
    
    1. **The Goal:** You have a procedural skyscraper facade with large wall panels, but also thin bevels and small decorative elements between them. You want to scatter window instances only on the large panels.
        
    2. **The Problem:** A standard Distribute Points on Faces node will place points randomly everywhere, including on the thin bevels where windows don't belong, which looks unrealistic.
        
    3. **The Solution:**
        
        - Use the Face Area node on your skyscraper mesh.
            
        - Use a Compare node to create a Boolean selection where the Area is greater than a certain threshold (e.g., 2.0 square meters). This isolates only the large wall panels.
            
        - Feed this Boolean selection into the Selection input of the Distribute Points on Faces node.
            
    4. **The Result:** Windows are now only instanced on the large, main faces of the building. The smaller, decorative or structural faces are automatically ignored. This creates a much more believable and art-directable result, as you can easily control the minimum size for a face to receive a window simply by adjusting the threshold value.