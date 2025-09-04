- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Rounds the sharp corners of a curve by replacing each corner point with a smooth, circular arc. This is the procedural equivalent of beveling vertices on a 2D mesh, but for curves.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve to be filleted.
        
    - **Radius (Socket - Input):** A float field that controls the size of the rounded corner. A larger radius creates a wider, smoother curve.
        
    - **Count (Socket - Input):** In 'Poly' mode, this integer controls how many new points are added to create the arc, determining its smoothness.
        
    - **Limit Radius (Socket - Input):** A Boolean. If True, it prevents the fillet radius from becoming so large that it overlaps with the next corner, avoiding ugly geometry artifacts.
        
    - **Mode (Property):**
        
        - **Bézier:** Creates a smooth, resolution-independent fillet using Bézier handles.
            
        - **Poly:** Creates a fillet with a specific number of new control points, giving direct control over the arc's segmentation.
            
    - **Curve (Socket - Output):** The curve with its corners rounded.
        
- **Practical Application:** This node is perfect for creating man-made paths with smooth, consistent turns, like a race track or a city road network.
    
    1. First, you create a road layout using a Curve Line or by drawing a Poly curve with sharp, 90-degree turns to block out the basic city grid.
        
    2. **The Problem:** The corners are unrealistically sharp.
        
    3. **The Solution:** Insert a Fillet Curve node. Set the Mode to 'Poly'.
        
    4. You can now provide a Radius value (e.g., 10 meters) to define how wide the turns should be. Set the Count to a reasonable number (e.g., 8) to create a smooth arc.
        
    5. Enable Limit Radius to ensure that corners in tight alleyways don't self-intersect.
        
    6. The result is that all the sharp corners of your road network are instantly replaced with smooth, perfect circular arcs. You can then use Curve to Mesh on this filleted curve to create the final road geometry, complete with smooth, drivable turns. This is a much faster and more precise workflow than trying to draw the curves manually.