- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Point
    
- **Core Function:** Generates a new point cloud "from scratch" where the position of each point is explicitly defined by a vector field input. Unlike the Distribute... nodes, this node does not require a surface or volume; it creates points in empty space.
    
- **Key Properties & Settings:**
    
    - **Count (Socket - Input):** An integer that specifies the total number of points to create.
        
    - **Position (Socket - Input):** The critical input. A vector field that defines the location for each point. Since there is no input geometry, this field can usually only depend on the Index of the point being created.
        
    - **Radius (Socket - Input):** A float field to set the radius attribute for each generated point.
        
    - **Points (Socket - Output):** The resulting point cloud.
        
- **Practical Application:** This node is perfect for creating points in a specific, mathematically defined arrangement, like a spiral galaxy or the orbiting electrons of a stylized atom.
    
    1. **The Goal:** To create a flat, spiral arrangement of points for a galaxy.
        
    2. Use the Points node. Set the Count to a high number, like 2000, for a dense spiral.
        
    3. **The Math:** You need to define the Position. A spiral can be defined by converting a polar coordinate (angle and distance) to a Cartesian coordinate (X and Y).
        
        - **Angle:** The Index of each point can be used to define its angle. Use a Map Range node to map the index (from 0 to 1999) to an angle range (e.g., from 0 to 1080 degrees, which is three full rotations).
            
        - **Distance:** The Index can also define the distance from the center. A simple Map Range from index to a radius (e.g., 0 to 10) will create a simple spiral.
            
        - Use Math nodes (Sine and Cosine) on the angle, then multiply them by the distance to get the final X and Y coordinates.
            
    4. Feed these calculated X and Y values (with Z=0) into a Combine XYZ node, and connect that to the Position input.
        
    5. **The Result:** A perfect, mathematically generated spiral of points. You can then instance stars onto these points to create a procedural galaxy, or use the same principle in 3D to create the helical structure of a DNA strand or the shell of a snail.