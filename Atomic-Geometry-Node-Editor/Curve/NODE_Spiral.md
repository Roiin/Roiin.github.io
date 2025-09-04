- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a poly spline in the shape of a spiral or helix.
    
- **Key Properties & Settings:**
    
    - **Resolution (Socket - Input):** An integer that controls how many points are in a single 360-degree rotation, determining the smoothness of the curve.
        
    - **Rotations (Socket - Input):** A float that controls the total number of full rotations the spiral makes.
        
    - **Start Radius, End Radius (Sockets - Input):** Floats that define the radius of the spiral at its start and end. The radius is linearly interpolated between these values, allowing for the creation of conical spirals.
        
    - **Height (Socket - Input):** A float that defines the total height of the spiral, stretching it along the Z-axis.
        
    - **Reverse (Socket - Input):** A boolean. If True, the spiral twists in a counter-clockwise direction instead of the default clockwise.
        
    - **Curve (Socket - Output):** The generated spiral curve.
        
- **Practical Application:** This node is perfect for creating mechanical springs or stylized, twisted animal horns.
    
    1. **For a Spring:**
        
        - Use the Spiral node. Keep Start Radius and End Radius the same (e.g., 0.1).
            
        - Set Rotations to a high number (e.g., 10) and Height to a value like 1.0.
            
        - Use a Curve to Mesh node with a small Curve Circle as the profile.
            
        - The result is a perfect, evenly coiled mechanical spring.
            
    2. **For an Animal Horn (like a Kudu):**
        
        - Use the Spiral node. Set the Start Radius to a larger value (e.g., 0.2) and the End Radius to a very small value (e.g., 0.01). This creates the conical taper.
            
        - Set Rotations to a moderate number (e.g., 3) and Height to a larger value (e.g., 2.0) to make it long and stretched out.
            
        - Use a Curve to Mesh node, but this time, use a Star or Quadrilateral as the profile to give the horn a more ridged, organic shape.
            
        - The result is a gracefully twisting, tapered horn, created with just a few simple parameters.