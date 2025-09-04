- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Converts a mesh into a point cloud by generating points at the location of its vertices, edges, faces, or face corners.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be converted.
        
    - **Selection (Socket - Input):** A boolean mask. Points will only be generated from elements where this is True.
        
    - **Position (Socket - Input):** An optional vector field to override the default position of the generated points.
        
    - **Radius (Socket - Input):** A float field to set the radius attribute for the output points, which controls their display size in the viewport.
        
    - **Mode (Property):** The core control determining where points are created:
        
        - **Vertices:** Creates one point at the location of each vertex.
            
        - **Edges:** Creates one point at the center of each edge.
            
        - **Faces:** Creates one point at the center of each face.
            
        - **Corners:** Creates a point for each face corner. (Note: multiple points will overlap at each vertex location).
            
    - **Points (Socket - Output):** The resulting point cloud.
        
- **Practical Application:** The 'Faces' mode is perfect for placing objects at the center of panels, like placing a bolt or rivet in the middle of every face of a metal animal's armor plate.
    
    1. Start with your procedural armor mesh, which is made up of many quad faces.
        
    2. **The Goal:** You want to instance a single rivet model in the exact center of every single face of the armor.
        
    3. Use the Mesh to Points node. Set its Mode to 'Faces'.
        
    4. The Points output is now a point cloud where each point is perfectly centered on a face of the original armor.
        
    5. Feed this point cloud into an Instance on Points node to place your rivet models.
        
    6. To align the rivets correctly, you need the normal of the original faces. You can capture this Normal attribute from the faces before the conversion and then transfer it to the points. Then use it with an Align Euler to Vector node to orient the rivets.
        
    7. The result is a perfectly riveted suit of armor, with each rivet precisely centered and oriented on its corresponding panel, which would be incredibly tedious to do by hand.