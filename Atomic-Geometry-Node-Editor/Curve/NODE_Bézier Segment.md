- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a single Bézier curve segment with two control points, defined by the explicit positions of the points and their corresponding handles. This is the most direct way to procedurally create a single, shaped curve.
    
- **Key Properties & Settings:**
    
    - **Resolution (Socket - Input):** The number of evaluated points to generate along the segment.
        
    - **Start, End (Sockets - Input):** Vector inputs for the positions of the two main control points.
        
    - **Start Handle, End Handle (Sockets - Input):** Vector inputs for the positions of the handles that control the segment's curvature.
        
    - **Mode (Property):**
        
        - **Position:** The handle inputs are treated as absolute world-space positions.
            
        - **Offset:** The handle inputs are treated as relative offsets from their parent control point. This is often more intuitive.
            
    - **Curve (Socket - Output):** The resulting single-segment Bézier curve.
        
- **Practical Application:** This node is perfect for procedurally generating and rigging simple limbs for a cartoon animal.
    
    1. Imagine you have the hip and ankle positions for an animal's leg as two vectors.
        
    2. Use the Bézier Segment node. The Start input is the hip position, and the End is the ankle position. If you connect nothing else, you get a straight line.
        
    3. To create a bent "knee," you need to control the handles. Set the Mode to 'Offset'.
        
    4. For the Start Handle, provide a vector that points slightly forward and down (e.g., [0, 0.5, -0.2]). For the End Handle, provide a vector that points slightly backward and up (e.g., [0, -0.5, 0.2]).
        
    5. The result is a single, gracefully curved segment that represents a bent leg. You can now easily animate the leg by moving the hip and ankle position vectors, and the curve of the leg will update automatically. You can then use Curve to Mesh on this output to give the leg thickness. This creates a simple but effective procedural leg rig.