- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a single parabolic curve segment defined by three control points: a Start and End that the curve passes through, and a Middle control point that the curve aims towards, defining its arc.
    
- **Key Properties & Settings:**
    
    - **Resolution (Socket - Input):** An integer that controls how many points are used to approximate the parabolic arc.
        
    - **Start, Middle, End (Sockets - "Input"):** Three vector inputs that define the shape of the curve.
        
    - **Curve (Socket - Output):** The resulting poly spline curve.
        
- **Practical Application:** This node is ideal for creating predictable, physics-based arcs, like the trajectory of a bouncing particle or a thrown object.
    
    1. Imagine you want to create a motion path for a ball bouncing between two points on the ground.
        
    2. Use the Quadratic Bézier node.
        
        - The Start position is the first bounce point on the ground (e.g., [-2, 0, 0]).
            
        - The End position is the second bounce point on the ground (e.g., [2, 0, 0]).
            
        - The Middle position defines the apex of the bounce. It would be the midpoint of the start and end, but raised in the air (e.g., [0, 0, 3]).
            
    3. The node automatically generates a perfect parabolic arc that starts on the ground, rises smoothly to its peak, and falls back to the ground at the endpoint.
        
    4. You can then animate a ball along this curve by sampling its position over time. This is a much more art-directable and mathematically stable way to create a bounce path compared to manually shaping a standard Bézier curve with handles.