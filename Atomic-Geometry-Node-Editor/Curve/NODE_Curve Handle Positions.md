- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** For each control point of a Bézier curve, this node outputs the precise location of its left and right handles. This allows for procedural analysis and manipulation of the curve's shape.
    
- **Key Properties & Settings:**
    
    - **Relative (Socket - Input):** A Boolean. If True, the handle positions are given as offsets relative to their parent control point. If False (the default), they are given in the object's local space.
        
    - **Left (Socket - Output):** A vector field representing the position of the left handle for each control point.
        
    - **Right (Socket - Output):** A vector field representing the position of the right handle for each control point.
        
- **Practical Application:** This node is essential for creating procedural geometry that intelligently interacts with a curve's shape. Imagine you have a main Bézier curve defining the graceful sweep of an octopus tentacle, and you want to procedurally add a row of suckers along its underside. You want the suckers to be larger and more pronounced where the tentacle bends sharply.
    
    1. First, use the Curve Handle Positions node (in Relative mode) on your tentacle curve.
        
    2. Calculate the Distance between the Left handle and the Right handle for each control point. A greater distance between the handles indicates a sharper, more influential curve at that point.
        
    3. This distance value can now be used as a scaling factor.
        
    4. When you use Instance on Points to place your sucker objects along the tentacle, you can feed this calculated handle-distance value into the Scale input.
        
    5. The result is that the suckers will be automatically larger and more prominent around the sharpest bends of the tentacle and smaller on the straighter sections, creating a more detailed and anatomically believable creature.