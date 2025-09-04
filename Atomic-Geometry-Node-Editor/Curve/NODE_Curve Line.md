- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a simple, straight poly spline with two control points.
    
- **Key Properties & Settings:**
    
    - **Mode (Property):**
        
        - **Points:** Defines the line by specifying the Start and End vector positions.
            
        - **Direction:** Defines the line by specifying a Start position, a Direction vector, and a Length.
            
    - **Start, End (Sockets - Input):** In Points mode, these vectors define the line's endpoints.
        
    - **Direction, Length (Sockets - Input):** In Direction mode, these define the line's orientation and size.
        
    - **Curve (Socket - Output):** The generated straight-line curve.
        
- **Practical Application:** This node is perfect for generating the radial support strands of a spider web.
    
    1. The center of the web is at the origin (0,0,0). You need lines that radiate outwards from this center.
        
    2. Use a Mesh Circle to create a set of points in a circle. These points will be the endpoints for your strands.
        
    3. Use a Repeat Zone or a similar method to iterate through each point of the mesh circle.
        
    4. Inside the loop, use the Curve Line node in Points mode.
        
        - The Start position is always the center of the web, a vector (0,0,0).
            
        - The End position is the position of the current point from your mesh circle.
            
    5. Use a Join Geometry node to collect the generated line from each iteration.
        
    6. The final output is a perfect set of straight lines radiating from a central point, forming the structural foundation of the spider web. This is a much more procedural and controllable method than drawing the lines by hand.