- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Adds new control points between the existing ones, increasing the density of the curve. Crucially, for Bézier and Poly splines, this is done without altering the curve's original shape. This is different from Resample Curve, which converts the curve to a Poly spline.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve to be subdivided.
        
    - **Cuts (Socket - Input):** An integer defining how many new points to add to the segment after each existing control point. A value of 1 will double the number of segments.
        
    - **Curve (Socket - Output):** The subdivided curve, now with more control points.
        
- **Practical Application:** This node is perfect for adding detail to specific parts of a curve while maintaining its original Bézier shape. Imagine you are creating the legs for a stylized animal, like a flamingo, using a simple 3-point Bézier curve for each leg to define the main pose.
    
    1. **The Goal:** You want to add a knobby, detailed knee joint in the middle of the leg, but you don't want to add extra points manually in Edit Mode because you want to keep the high-level control of the 3-point Bézier for easy posing.
        
    2. Use the Subdivide Curve node with Cuts set to 1. This adds a new control point right in the middle of the main leg segments without changing the leg's overall shape.
        
    3. You now have points at the hip, the new knee, and the ankle. You can create a selection for just the new "knee" point (e.g., by its index).
        
    4. Use this selection with a Set Curve Radius node to increase the radius only at the knee.
        
    5. When you use Curve to Mesh, the leg will now have a pronounced, thicker section in the middle, creating a convincing knee joint. The best part is that you can still go back to Edit Mode and move the original three Bézier points to change the flamingo's pose, and the procedural knee will automatically stay in the correct relative position.