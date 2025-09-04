- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Sample)
    
- **Core Function:** Projects rays from a set of source positions in a specific direction to find the first intersection point on a separate target geometry, providing detailed information about the hit.
    
- **Key Properties & Settings:**
    
    - **Target Geometry (Socket - Input):** The geometry that the rays will be cast against.
        
    - **Source Position (Socket - Input):** The starting point for each individual ray.
        
    - **Ray Direction (Socket - Input):** A vector field defining the direction each ray travels.
        
    - **Ray Length (Socket - Input):** The maximum distance a ray can travel. If no surface is hit within this distance, it's considered a miss.
        
    - **Is Hit (Socket - Output):** The most critical output; a boolean that is True for each ray that successfully intersected the target geometry.
        
    - **Hit Position (Socket - Output):** The world-space location of the intersection point on the target's surface.
        
    - **Hit Normal (Socket - Output):** The surface normal vector of the target geometry at the point of intersection. This is essential for aligning objects to a surface.
        
    - **Hit Distance (Socket - Output):** The distance from the Source Position to the Hit Position.
        
    - **Attribute (Socket - Output):** If an attribute was sampled (e.g., vertex color from the target), this socket outputs its value at the hit location.
        
- **Practical Application:** This node is perfect for realistically placing objects onto complex, uneven surfaces. Imagine you want to procedurally place barnacles onto the curved hull of a shipwreck model.
    
    1. Create a flat Grid of points positioned above the shipwreck hull. This grid will be the source of our rays.
        
    2. Use the Raycast node. The Target Geometry is the shipwreck hull. The Source Position is the position of each point on our grid. The Ray Direction is a vector pointing straight down (0, 0, -1).
        
    3. The Is Hit output can be used to delete any points from our grid that missed the hull entirely.
        
    4. Use a Set Position node on the remaining grid points. For the new position, use the Hit Position output from the Raycast node. This snaps every point perfectly onto the shipwreck's surface.
        
    5. Finally, use Instance on Points to place your barnacle models. For the Rotation input, use an Align Euler to Vector node and plug the Hit Normal into it. This ensures every single barnacle is perfectly oriented to be flush with the curved surface of the hull, creating a highly realistic result.