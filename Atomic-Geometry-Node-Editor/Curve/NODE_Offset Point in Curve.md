- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Topology)
    
- **Core Function:** For any given control point, this node finds the index of another point on the same spline by "walking" a specified number of steps forward or backward along the curve.
    
- **Key Properties & Settings:**
    
    - **Point Index (Socket - Input):** The index of the starting point for the "walk". Defaults to the current point being evaluated.
        
    - **Offset (Socket - Input):** An integer defining how many steps to take. Positive values move towards the end of the spline; negative values move towards the start.
        
    - **Is Valid Offset (Socket - Output):** A boolean that is True only if the offset "walk" lands on a valid point. For a non-cyclic curve, an offset from the last point will be invalid. This is crucial for preventing errors.
        
    - **Point Index (Socket - Output):** The index of the point that was found after the offset was applied.
        
- **Practical Application:** This node is perfect for creating geometry that connects adjacent points, like the body segments of a centipede.
    
    1. First, create a long, resampled Curve Line to serve as the centipede's spine. The points on this curve are where the legs will attach.
        
    2. **The Goal:** You want to create the chitinous armor plates that span the gap between each leg joint.
        
    3. For each point on the curve (let's call its index i), you need to find the next point in the sequence (index i+1).
        
    4. Use the Offset Point in Curve node. The Point Index is the current Index. The Offset is a constant value of 1.
        
    5. The Point Index output of this node now gives you the index of the next point in the line for every point on the curve.
        
    6. Use two Sample Index nodes: one to get the Position of the current point (i), and one to get the Position of the next point (i+1).
        
    7. You now have the start and end points for each body segment. You can feed these into a Curve Line node and then a Curve to Mesh node to create a solid plate.
        
    8. Use the Is Valid Offset output as the selection for your geometry creation. This ensures that you don't try to create a segment starting from the very last point of the curve, which has no "next" point.