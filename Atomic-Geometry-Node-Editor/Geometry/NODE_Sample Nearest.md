- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Sample)
    
- **Core Function:** For each point in the source geometry, it searches a separate target geometry and finds the index of the single closest element (vertex, edge, or face).
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The target geometry to be searched.
        
    - **Sample Position (Socket - Input):** The location(s) from which to start the search.
        
    - **Domain (Property):** The element type to search for on the target geometry (Points, Edges, Faces).
        
    - **Index (Socket - Output):** The primary output; an integer field containing the index of the closest element found on the target geometry.
        
- **Practical Application:** This is the key to transferring attributes between two unrelated meshes based on proximity. Imagine you have a detailed animal model (the "skin") that has been carefully texture-painted with vertex colors (e.g., brown and white patches for a cow). You then create a separate particle system of hair curves (the "fur") that covers the skin. You want the fur to inherit the color of the skin directly underneath it.
    
    1. On the fur object, use the Sample Nearest node. The Geometry input is the painted "skin" mesh. The Sample Position is the root position of each hair curve. The node now finds the Index of the closest vertex on the skin for each hair.
        
    2. Next, feed this Index output into a Sample Index node. For this second node, the Geometry is again the "skin" mesh, and the Value you want to read is its vertex color attribute ("Color").
        
    3. The result is that you have successfully transferred the color from the skin to the fur. You can now store this color as an attribute on the fur curves and use it in the shader, ensuring the fur's color pattern perfectly matches the underlying skin.