- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Write)
    
- **Core Function:** Sets the per-point radius attribute on a curve, which controls the thickness or scale of geometry generated from it (e.g., in a Curve to Mesh node).
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The curve geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. The radius will only be set on control points where this is True.
        
    - **Radius (Socket - Input):** A float field that provides the new radius value for each selected control point.
        
    - **Geometry (Socket - Output):** The curve, now with the updated radius attribute.
        
- **Practical Application:** This node is essential for creating organic shapes that taper, like the branches of a tree.
    
    1. You start with a curve object that represents the structure of a tree branch, from its base to its tip.
        
    2. To give it physical thickness, you will use a Curve to Mesh node. But first, you need to define its shape.
        
    3. Insert the Set Curve Radius node before the Curve to Mesh node.
        
    4. To create the tapering effect, you need a gradient that goes from thick at the start to thin at the end. The Spline Parameter node is perfect for this.
        
    5. Use a Math node to invert the Factor output of the Spline Parameter node (1 - Factor). This gives you a gradient from 1.0 (at the start) to 0.0 (at the end).
        
    6. You can use another Math node (Multiply) to control the overall maximum thickness of the branch base.
        
    7. Feed this final calculated gradient into the Radius input of the Set Curve Radius node.
        
    8. The result is a branch that is thickest where it connects to the trunk and becomes progressively thinner towards the tip, creating a natural and realistic shape.