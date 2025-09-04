- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Generates a simplified, "shrink-wrapped" convex mesh that completely encloses all the vertices of an input geometry. Note: For instanced geometry, it creates a separate hull for each instance; to get a single hull for the entire collection, first use a Realize Instances node.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry (often a point cloud or complex mesh) to be enclosed.
        
    - **Convex Hull (Socket - Output):** The resulting simplified, convex mesh.
        
- **Practical Application:** This node is fantastic for creating "metaball" or amorphous, blobby creatures from a cloud of particles.
    
    1. First, generate a cloud of points. You can do this by using Distribute Points on Faces on a mesh, then use a Set Position node driven by an animated Noise Texture (using Scene Time) to make the points move and swarm around.
        
    2. Feed this animated cloud of points directly into the Convex Hull node's Geometry input.
        
    3. The output will be a single, lumpy mesh that is constantly changing its shape to contain the moving particles. The raw output will be low-poly and faceted.
        
    4. To create a smooth, organic look, connect a Subdivision Surface node and a Set Shade Smooth node after the Convex Hull.
        
    5. The final result is a single, smooth, animated mesh that looks like a shifting, amorphous slime creature, all generated from a simple particle cloud. This is a powerful technique for creating stylized liquid effects or otherworldly animals.