- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** For each spline, this node outputs its resolution, which is the integer value determining how many evaluated points are generated between each pair of control points for Bézier and NURBS splines. It has no effect on Poly splines.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Resolution (Socket - Output):** An integer field representing the resolution value for each spline.
        
- **Practical Application:** This node allows a procedural setup to intelligently adapt to the quality settings of an input curve. Imagine you are creating a generic "Particle Emitter" node group that instances particles along any input curve.
    
    1. **The Goal:** You want the number of emitted particles to automatically increase as the user increases the curve's resolution in the Blender properties panel, ensuring a dense particle trail for high-quality curves and a sparse one for low-quality curves without needing a separate "Particle Count" slider.
        
    2. Use the Spline Resolution node to get the resolution of the input curve (e.g., 12 for the default Bézier).
        
    3. Use the Spline Length node to get the curve's Point Count (the number of control points).
        
    4. Multiply the Resolution by the Point Count. This gives you a rough but effective approximation of the total number of visible points on the curve.
        
    5. You can then use this calculated value to drive the Count input of a Resample Curve node.
        
    6. The result is a smart particle system. If the artist provides a low-resolution curve, few particles are generated, keeping the viewport fast. If they increase the curve's resolution to make it smoother, your node group automatically reads this new value and increases the particle count to match, maintaining a consistent density without any manual adjustments.