- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Write)
    
- **Core Function:** Converts the selected splines to a different underlying mathematical type (Bézier, NURBS, Poly, or Catmull-Rom), which changes how the curve is interpolated between its control points (e.g., smooth vs. sharp).
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The curve geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. The type will only be changed on splines where this is True.
        
    - **Spline Type (Property):** A dropdown menu to choose the target spline type to convert to.
        
    - **Curve (Socket - Output):** The curve, now with its splines converted to the new type.
        
- **Practical Application:** This node is perfect for establishing the visual character of a curve, like creating a lightning bolt.
    
    1. You might start with a smooth Bézier curve drawn from the sky to the ground to define the main path of the bolt. This curve is too smooth and organic for a lightning effect.
        
    2. **The Goal:** To make the path sharp and angular.
        
    3. Insert a Set Spline Type node and set the Spline Type to 'Poly'. This instantly converts the smooth arc into a series of straight, connected line segments between the original control points. This forms the primary, low-frequency jaggedness.
        
    4. You can then use Resample Curve to add many more points along this new poly-line and then a Set Position node with a high-frequency Noise Texture to add the chaotic, smaller zigs and zags.
        
    5. The key is that by first converting the base curve to 'Poly', the final displaced shape is inherently sharp and angular, which is characteristic of lightning, rather than the wobbly, wavy result you'd get from displacing a smooth curve type.