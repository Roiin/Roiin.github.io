- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Fills closed curves with mesh geometry, creating flat, 2D faces using a triangulation algorithm. It can intelligently create holes when curves are nested inside one another.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve(s) to be filled. The curves should be closed (cyclic) for predictable results.
        
    - **Group ID (Socket - Input):** An integer field. Curves sharing the same Group ID will be filled as a single system (allowing for holes), while curves with different IDs will be filled independently.
        
    - **Mode (Property):**
        
        - **Triangles:** Fills the area with a mesh of triangles.
            
        - **N-gons:** Fills the area with as few N-gons as possible, resulting in cleaner topology for flat surfaces.
            
    - **Mesh (Socket - Output):** The resulting 2D mesh geometry.
        
- **Practical Application:** This node is perfect for creating complex flat surfaces with cutouts, like a stained glass window.
    
    1. First, you create a curve object that contains multiple separate, closed splines. One large spline defines the outer rectangular frame of the window. Several smaller splines inside it define the intricate patterns for the colored glass.
        
    2. Feed this entire curve object into the Fill Curve node and set the Mode to 'N-gons'.
        
    3. By default, all curves are in the same group. The node is smart enough to recognize that the smaller splines are inside the larger one. It will fill the area between the outer frame and the inner patterns, automatically creating holes where the inner patterns are.
        
    4. To create the different colored glass pieces, you can use the Separate Geometry node on the original curves before filling them. You separate the outer frame from the inner patterns.
        
    5. You can then Fill Curve on each set of curves independently and assign different materials (one for the lead frame, one for the colored glass) before joining them back together. The result is a complex, multi-material stained glass window generated entirely from a simple 2D curve outline.