- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Write)
    
- **Core Function:** Sets the per-point tilt attribute on a curve, which defines the rotation (in radians) of the curve's normal around its tangent. This is the primary method for procedurally adding "twist" to a curve.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The curve geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. The tilt will only be set on control points where this is True.
        
    - **Tilt (Socket - Input):** A float field that provides the new tilt angle (in radians) for each selected control point.
        
    - **Geometry (Socket - Output):** The curve, now with the updated tilt attribute.
        
- **Practical Application:** This node is perfect for creating spiraling or coiled objects, like a rope or an octopus tentacle with suckers.
    
    1. Start with a Curve Line primitive to create a straight curve.
        
    2. To create the coiled shape, you'll place a non-circular profile on it with Curve to Mesh. For example, use a Star primitive with 3 points to create a triangular "rope" profile.
        
    3. **The Problem:** By default, the profile is extruded straight, creating a simple triangular prism.
        
    4. **The Solution:** Insert a Set Curve Tilt node before the Curve to Mesh node.
        
    5. To create a continuous twist, you need a value that increases along the curve. The Spline Parameter node's Length output is perfect for this. It gives a value that smoothly increases from 0 at the start to the curve's total length at the end.
        
    6. Connect this Length output to the Tilt input. You can multiply this value by a constant to control the "tightness" of the twist.
        
    7. The result is that the triangular profile now twists around the curve as it travels along its length, creating a perfect, procedurally generated twisted rope. This same technique could be used to control the rotation of instanced suckers along a tentacle curve.