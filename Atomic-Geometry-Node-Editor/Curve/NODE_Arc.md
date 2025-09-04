- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a circular poly spline arc, with two modes for defining its shape: Radius (using angles and a radius) or Points (defining the arc by three points it must pass through).
    
- **Key Properties & Settings:**
    
    - **Mode (Property):**
        
        - **Radius:** Defines the arc using a Radius, Start Angle, and Sweep Angle. This is best for precise, numerical creation.
            
        - **Points:** Defines the arc using three input vectors: Start, Middle, and End. This is best for snapping the arc to existing geometry.
            
    - **Resolution (Socket - Input):** An integer controlling how many points/edges are used to create the arc.
        
    - **Connect Center (Socket - Input):** A Boolean. If True, it adds extra lines from the arc's endpoints to its center, creating a "pie slice" shape.
        
    - **Curve (Socket - Output):** The generated arc curve.
        
    - **Center, Normal, Radius (Sockets - Output):** In Points mode, these sockets provide the calculated center, normal, and radius of the arc, which is useful for further procedural constructions.
        
- **Practical Application:** The Arc node is perfect for creating the curved threads of a spider web.
    
    1. First, you create the main radial support strands of the web using a Star curve primitive. Resample this star to create the points where the web's spiral threads will attach.
        
    2. **The Goal:** You need to connect these attachment points with curved, sagging threads, not straight lines.
        
    3. You can iterate through the attachment points. For each point (P1) and its neighbor on the next radial strand (P2), you have the start and end of your arc.
        
    4. To create the sag, you need a Middle point. You can calculate this by finding the midpoint between P1 and P2 and then offsetting it slightly towards the center of the web.
        
    5. Use the Arc node in Points mode. The Start is P1, the End is P2, and the Middle is your calculated sagging point.
        
    6. By generating an arc for each pair of adjacent points on the radial strands, you can construct a realistic, sagging spiral web. The Points mode ensures that each thread perfectly connects to its anchor points, even if the radial strands aren't perfectly symmetrical.