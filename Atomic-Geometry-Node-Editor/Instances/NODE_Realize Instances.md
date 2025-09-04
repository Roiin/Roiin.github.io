- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** Converts lightweight instances into "real," unique geometry. This "unpacks" the instances, creating a single, large mesh where every point, edge, and face can be manipulated individually. This is necessary for operations like sculpting, vertex painting, or procedural effects that need to access the underlying mesh topology, but it comes at a significant performance cost.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry containing instances to be realized.
        
    - **Selection (Socket - Input):** A boolean mask. Only selected instances will be converted into real geometry.
        
    - **Geometry (Socket - Output):** The final geometry, which is now a single, potentially very heavy, mesh or curve object. Any attributes from the instances (like scale or a random ID) are transferred down to the points/faces of the new mesh.
        
- **Practical Application:** This node is essential when you need to apply a final, mesh-based effect to an instanced scene, such as adding procedural snow cover to a forest.
    
    1. First, you create a large, efficient forest using the Instance on Points node, scattering instanced trees.
        
    2. **The Goal:** You want to add a layer of snow that realistically settles on the upward-facing surfaces of all the trees, treating the entire forest as one single object.
        
    3. **The Problem:** You cannot calculate ambient occlusion or check the world-space normals of the tree branches while they are instances, because the underlying geometry doesn't "exist" in a way that mesh-based nodes can see.
        
    4. **The Solution:**
        
        - Insert a Realize Instances node after your forest is generated. **Warning:** This will make the scene much heavier, so it should be one of the last steps.
            
        - The output is now a single, massive mesh containing all the trees.
            
        - Now, you can use nodes that operate on mesh data. You can take the Normal of every face in this new mesh, compare it to a world "up" vector to find all the upward-facing surfaces, and use this selection to procedurally place a "snow" material or even displace the geometry to create snow drifts.
            
    5. The Realize Instances node was the necessary, performance-heavy step that enabled the final, high-detail mesh-based effect.