**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Read)

**Core Function:** Provides specific information about the last point (the "tip") of each hair curve.

**Key Properties & Settings:**

- **Tip Selection (Output):** A boolean field that is True only for the final control point of every curve and False for all other points.
    
- **Tip Position (Output):** The 3D position vector of the tip point of each curve.
    
- **Tip Direction (Output):** The tangent vector of the very last segment of the curve, indicating the direction the hair is pointing at its end.
    
- **Tip Index (Output):** The index of the tip point within the overall list of all points in the curve geometry component.
    

**Practical Application:**  
This node is the direct counterpart to the Curve Root node and is essential for creating effects that occur only at the ends of hairs or curves. A classic example is adding flowers or fruits to the ends of the branches of a procedural tree.

- **The Goal:** To instance a single flower model at the exact tip of every terminal branch of a procedural tree.
    
- **The Problem:** The tree is a complex geometry made of many curves. If you try to instance flowers on the tree's points, they will appear all along the branches and trunk, not just at the ends where flowers naturally grow. You need a way to select only the final point of each curve.
    
- **The Solution:** The Curve Tip node provides the precise selection needed.
    
    1. Start with your procedurally generated tree geometry (composed of curves).
        
    2. Add an Instance on Points node, connecting the tree curves to the Points input.
        
    3. Add a Curve Tip node.
        
    4. Connect its Tip Selection output directly into the Selection input of the Instance on Points node.
        
    5. Use a flower model as the Instance geometry.
        

The Instance on Points node will now only create flowers where the Tip Selection is True. This ensures that a flower is placed perfectly at the tip of every single branch, creating a natural-looking and efficient result.