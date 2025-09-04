- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Splits a single, potentially mixed geometry data-stream into its fundamental component types, isolating meshes, curves, point clouds, etc., into their own separate outputs.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry, which may contain multiple data types combined with a Join Geometry node.
        
    - **Mesh (Socket - Output):** The mesh part of the input geometry.
        
    - **Curve (Socket - Output):** The curve part of the input geometry.
        
    - **Point Cloud (Socket - Output):** The point cloud part of the input geometry.
        
    - **Volume (Socket - Output):** The volume part of the input geometry.
        
    - **Instances (Socket - Output):** Outputs all top-level instances. To access the geometry inside the instances, a Realize Instances node must be used first.
        
- **Practical Application:** This node is essential when you need to apply different procedural operations to different types of geometry that have been combined. Imagine creating a decorative arched window.
    
    1. You have a mesh for the solid stone frame and a separate curve object for the delicate ironwork grill inside it. You use Join Geometry to treat them as a single unit for initial positioning.
        
    2. **The Problem:** Now, you want to give the ironwork thickness (which requires curve-specific nodes) and bevel the edges of the stone frame (which requires mesh-specific nodes). You can't do this while they are combined in a single data stream.
        
    3. **The Solution:** You feed the combined geometry into the Separate Components node.
        
        - The Mesh output (the stone frame) is now isolated and can be sent to an Extrude Mesh or Bevel node to add detail.
            
        - The Curve output (the ironwork grill) is also isolated and can be sent to a Curve to Mesh node to give it a circular profile and physical thickness.
            
    4. Finally, you use a second Join Geometry node to recombine the now-properly-modified components into the final, complete window asset.