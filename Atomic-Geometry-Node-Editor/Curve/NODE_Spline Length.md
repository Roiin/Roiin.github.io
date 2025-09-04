- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** For curve objects containing multiple splines, this node outputs the length and point count of each individual spline, rather than the total for the whole object.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Length (Socket - Output):** A float field. For every control point on a spline, this value will be the total length of that specific spline.
        
    - **Point Count (Socket - Output):** An integer field. For every control point on a spline, this value will be the total number of control points in that specific spline.
        
- **Practical Application:** This node is perfect for creating procedural creatures where different body parts are defined by separate splines. Imagine you are creating a simple spider where the body is a sphere and the legs are a curve object containing eight separate splines drawn in Edit Mode.
    
    1. **The Goal:** You want to give the legs a natural taper, making them thicker at the base (where they connect to the body) and thinner at the tip. The thickness should be proportional to the length of each leg, so longer legs are inherently thicker.
        
    2. Use the Spline Length node on your leg curve object. The Length output now gives you the total length for each of the eight leg splines.
        
    3. Use a Spline Parameter node to get the Factor (a 0-to-1 gradient along each spline). Invert this so it's 1 at the start and 0 at the end.
        
    4. Multiply the inverted Factor by the Spline Length. The result is a value that is large at the start of each leg (equal to its length) and fades to zero at the tip.
        
    5. Feed this final value into a Set Curve Radius node. The result is that each of the eight legs will now have a radius that is perfectly tapered from thick to thin, and the overall thickness of each leg is automatically proportional to how long you drew it in Edit Mode, making for a very quick and art-directable workflow.