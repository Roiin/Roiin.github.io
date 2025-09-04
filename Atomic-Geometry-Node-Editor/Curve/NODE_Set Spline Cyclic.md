- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Write)
    
- **Core Function:** For each spline in a curve, this node programmatically sets whether it is an open path or a closed loop (cyclic).
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The curve geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. The cyclic property will only be changed on splines where this is True.
        
    - **Cyclic (Socket - Input):** A Boolean value. If True, the selected splines will become closed loops. If False, they will become open paths.
        
    - **Geometry (Socket - Output):** The curve, now with its splines' cyclic state updated.
        
- **Practical Application:** This node is great for creating interactive or switchable procedural assets. Imagine you have a particle system where you want particles to follow a path. You want a simple checkbox in your modifier panel to switch the path between a "patrol" (back and forth) and an "orbit" (continuous loop).
    
    1. Start with a Curve Circle primitive. This is a closed, cyclic curve.
        
    2. Use a Group Input node to create a Boolean checkbox input in the modifier panel called "Is Orbit".
        
    3. Feed the Geometry from the curve circle into the Set Spline Cyclic node.
        
    4. Connect the "Is Orbit" checkbox directly to the Cyclic input of the node.
        
    5. Now, the curve's topology is directly controlled by the UI checkbox.
        
        - If "Is Orbit" is checked (True), the circle remains a closed loop, and any particles animated along it will orbit continuously.
            
        - If "Is Orbit" is unchecked (False), the Set Spline Cyclic node breaks the circle, turning it into an open arc. Now, the same particle animation will cause the particles to travel from one end to the other and then stop (or reverse, depending on your setup).
            
    6. This creates a versatile and user-friendly tool without needing to switch between different curve objects.