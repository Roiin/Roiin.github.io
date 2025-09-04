- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a closed, star-shaped poly spline by creating points on an inner and outer circle and connecting them in an alternating sequence.
    
- **Key Properties & Settings:**
    
    - **Points (Socket - Input):** An integer that defines how many points the star will have. This is the number of points on both the inner and outer circles.
        
    - **Inner Radius (Socket - Input):** The radius of the inner circle, defining how close the "valleys" of the star are to the center.
        
    - **Outer Radius (Socket - Input):** The radius of the outer circle, defining the position of the star's "tips".
        
    - **Twist (Socket - Input):** An angle (in radians) that rotates the inner set of points. A value of zero creates a symmetrical star. Twisting it can create more dynamic, shuriken-like shapes.
        
    - **Curve (Socket - Output):** The generated star-shaped curve.
        
    - **Outer Points (Socket - Output):** A boolean attribute that is True for the points at the tips of the star (on the outer radius) and False for the points in the valleys (on the inner radius).
        
- **Practical Application:** This node is perfect for creating procedural gears or spiky particle effects.
    
    1. **For a Gear:**
        
        - Use the Star node. Set the Points to a high number, like 20.
            
        - Keep the Inner Radius and Outer Radius relatively close to each other (e.g., 0.9 and 1.0) to create short, blocky teeth.
            
        - Use a Fill Curve node on the output to create a solid 2D shape.
            
        - Use an Extrude Mesh node to give the gear thickness.
            
    2. **For Stylized Animal Eyes:**
        
        - The Outer Points selection is key here. Imagine creating a stylized, spiky iris for a dragon's eye.
            
        - Create a Star with 8 points.
            
        - Use Curve to Points to create a point cloud from the star shape.
            
        - Use the Outer Points selection to drive a Switch node.
            
        - You can then instance two different shapes: a large, sharp cone on the True (outer) points, and a small sphere on the False (inner) points.
            
        - The result is a complex, spiky iris made of two different, intelligently placed shapes, all controlled by a single Star primitive.