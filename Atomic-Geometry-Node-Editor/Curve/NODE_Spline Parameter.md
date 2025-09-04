- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** For each point on a spline, this node outputs its position along the spline's length, provided as a normalized 0-to-1 Factor, a measured Length, and a per-spline Index. Note: For predictable, evenly spaced results, it is highly recommended to use a Resample Curve node first to create a poly spline where control points match the evaluated points.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Factor (Socket - Output):** The most common output. A float gradient from 0.0 (start of the spline) to 1.0 (end of the spline), calculated based on the curve's length.
        
    - **Length (Socket - Output):** The measured distance from the start of the spline to the current control point.
        
    - **Index (Socket - Output):** The index of the control point within its own spline, starting from 0. This differs from the global Index node.
        
- **Practical Application:** This node is the primary tool for creating gradients along a curve's length, perfect for effects like tapering an animal's tail.
    
    1. Start with a single Bézier curve that defines the shape and pose of a scorpion's tail.
        
    2. To give it thickness, you will use a Set Curve Radius node followed by a Curve to Mesh node.
        
    3. Connect the Factor output of the Spline Parameter node into the Radius input of the Set Curve Radius node.
        
    4. **The Problem:** This creates a tail that is thin at the base (Factor=0) and thick at the tip (Factor=1), which is the opposite of what's natural.
        
    5. **The Solution:** You need to invert the gradient. The easiest way is with a Math node set to 'Subtract'. Plug the Factor into the bottom socket and set the top value to 1.0 (Result = 1 - Factor).
        
    6. Feed this inverted gradient into the Set Curve Radius node instead. You can multiply it by another value (e.g., 0.2) to control the overall maximum thickness.
        
    7. The result is a perfectly tapered scorpion tail that is thickest where it connects to the body and thins out elegantly towards the stinger. The entire tapering effect is controlled procedurally by the Spline Parameter node's gradient.