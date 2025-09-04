- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** Generates a boolean selection that is True for a specified number of control points at the start and/or end of each individual spline within a curve object.
    
- **Key Properties & Settings:**
    
    - **Start Size (Socket - Input):** An integer defining how many points to select from the beginning of each spline (index 0 onwards).
        
    - **End Size (Socket - Input):** An integer defining how many points to select from the end of each spline.
        
    - **Selection (Socket - Output):** The primary output; a boolean field that is True for the specified endpoints.
        
- **Practical Application:** This node is perfect for adding special effects to the beginning or end of a curve. Imagine creating a magical particle effect that leaves a glowing trail. You want the trail to have a bright, large "head" particle and fade out to nothing at the tail.
    
    1. First, create your trail using a curve object. Use Resample Curve to create a dense series of points along it.
        
    2. Use the Endpoint Selection node on this resampled curve. Set the Start Size to 1 and the End Size to 0. The Selection output is now True only for the very first point of the curve.
        
    3. Use a Switch node. For its Switch input, use the Selection from the Endpoint Selection node.
        
    4. Into the True input of the Switch node, feed a large value (e.g., 2.0). Into the False input, feed a smaller value (e.g., 0.5). The Switch node now outputs 2.0 for the head of the trail and 0.5 for the rest.
        
    5. You can use this output to control the Scale of particles instanced on the curve, or you can capture it as an attribute to control the emission strength or size in the shader. The result is a trail with a distinctly large, bright head that leads the rest of the effect, which is a common and visually appealing look.