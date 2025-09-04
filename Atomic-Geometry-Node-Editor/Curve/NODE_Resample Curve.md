- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Reconstructs a curve by generating a new set of control points, converting the spline to a Poly type in the process. In 'Count' and 'Length' modes, these new points are distributed evenly, which is essential for creating predictable spacing for instanced objects.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve to be resampled.
        
    - **Selection (Socket - Input):** A boolean mask. Only splines where this is True will be resampled.
        
    - **Mode (Property):** The method used to determine the new point distribution:
        
        - **Count:** Creates a specific, user-defined number of points, spaced evenly along the curve's length.
            
        - **Length:** Creates points spaced apart by a specific, user-defined distance. The number of points is calculated automatically. This is often the most intuitive mode.
            
        - **Evaluated:** Creates a new control point for each of the original curve's visible evaluated points. This is useful for "baking in" the resolution of a Bézier or NURBS curve.
            
    - **Curve (Socket - Output):** The new, resampled poly spline.
        
- **Practical Application:** This node is fundamental for creating objects with regular, repeating elements, like the wooden ties on a railroad track.
    
    1. First, you draw a long, winding Bézier curve to define the path of the railway.
        
    2. **The Problem:** The evaluated points on a Bézier curve are not evenly spaced; they are denser around sharp corners. If you instance ties directly onto this curve, they will bunch up in the turns and be sparse on the straight sections, which is incorrect.
        
    3. **The Solution:** Insert the Resample Curve node after your main path curve.
        
    4. Set the Mode to 'Length'.
        
    5. Set the Length value to the desired spacing between ties, for example, 0.4 meters.
        
    6. The output of this node is a new curve where the points are now perfectly and consistently spaced 0.4 meters apart, regardless of the curve's shape.
        
    7. You can now feed this resampled curve into an Instance on Points node to place your wooden tie models. The result is a perfect, evenly spaced railroad track bed that will automatically update correctly if you ever change the shape or length of the master path curve.