- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a closed, four-sided curve (a quadrilateral) with several preset modes for common shapes like rectangles, trapezoids, and kites, or from four explicitly defined points.
    
- **Key Properties & Settings:**
    
    - **Mode (Property):** The primary control that determines the shape and available inputs:
        
        - **Rectangle:** A standard rectangle defined by Width and Height.
            
        - **Parallelogram:** A skewed rectangle, controlled by Width, Height, and Offset.
            
        - **Trapezoid:** A four-sided shape with parallel top and bottom edges, defined by Top Width, Bottom Width, Height, and Offset.
            
        - **Kite:** A classic kite shape.
            
        - **Points:** Creates a custom quadrilateral by directly connecting four input Point vectors.
            
    - **Width / Height (Sockets - Input):** Control the size of the shape in the relevant modes.
        
    - **Offset (Socket - Input):** Controls the horizontal skew in Parallelogram and Trapezoid modes.
        
    - **Point 1, Point 2, Point 3, Point 4 (Sockets - Input):** In Points mode, these four vectors define the corners of the quadrilateral.
        
    - **Curve (Socket - Output):** The generated four-sided poly spline.
        
- **Practical Application:** This node is perfect for quickly creating procedural window frames.
    
    1. To create a standard, modern window, you would use the Quadrilateral node in its default Rectangle mode.
        
    2. To create a more stylized, fantasy-style window for a crooked house, you can switch the Mode to 'Trapezoid'. By setting the Bottom Width to be slightly wider than the Top Width and giving it a small Offset, you can create a non-symmetrical, slightly skewed outline.
        
    3. This single curve is the main outline of your window. To turn it into a solid frame, you can use a Curve to Mesh node. For the Profile Curve input, you can use a second, much smaller Quadrilateral node set to 'Rectangle' mode.
        
    4. The result is a complete, 3D window frame with a unique, non-symmetrical shape that would be tedious to model manually. You can easily create variations by adjusting the width and offset parameters.