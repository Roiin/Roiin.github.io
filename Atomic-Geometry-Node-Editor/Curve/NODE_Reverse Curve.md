- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** For each selected spline, this node reverses its internal direction, swapping its start and end points. The visual shape of the curve remains identical.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve to be reversed.
        
    - **Selection (Socket - Input):** A boolean mask. Only splines where this is True will have their direction flipped.
        
    - **Curve (Socket - Output):** The curve with its selected splines reversed.
        
- **Practical Application:** This node is essential when the "flow" or "direction" of an effect matters. Imagine you have a river path defined by a curve, and you are animating particles (like debris or fish) along it by animating the Factor of a Sample Curve node from 0 to 1.
    
    1. **The Problem:** After setting up the animation, you realize the river is flowing uphill, or your school of fish is swimming backwards along the path. The curve was drawn in the wrong direction.
        
    2. **The Solution:** Instead of going into Edit Mode to manually switch the curve's direction (which can be destructive or tedious), you can simply insert a Reverse Curve node into your node tree before the animation logic.
        
    3. The node instantly flips the curve's start and end points. Now, when your animation drives the sample Factor from 0 to 1, the particles will travel in the opposite, correct direction, flowing downhill or swimming forwards. This allows for a quick, non-destructive fix to directional problems.