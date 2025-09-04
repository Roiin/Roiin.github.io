- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** For each control point on a curve, this node outputs the normalized tangent vector, which is the direction the curve is pointing at that specific location. Note: For Bézier/NURBS curves, this evaluates at the control points, not the visible, interpolated points. For predictable results, it's often best to use a Resample Curve node first to create a poly spline.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Tangent (Socket - Output):** A normalized vector field representing the forward direction of the curve at each point.
        
- **Practical Application:** This node is essential for orienting instanced objects so they "follow" the curve's path. Imagine creating an animation of a school of fish swimming along a complex, winding curve.
    
    1. First, use a Resample Curve node on your path to create a series of evenly spaced points to represent the fish locations.
        
    2. Use an Instance on Points node to place a fish model at each of these points.
        
    3. **The Problem:** By default, all the fish will be pointing in the same direction (e.g., along the Y-axis), which looks completely unnatural as they move around corners.
        
    4. **The Solution:** Use the Curve Tangent node. This gives you the forward-facing direction of the path at every single point.
        
    5. Feed this Tangent vector into an Align Euler to Vector node. Set the 'Axis' to 'Y' (or whichever axis your fish model points along).
        
    6. Connect the Rotation output of the Align Euler to Vector node to the Rotation input of your Instance on Points node.
        
    7. The result is that every single fish is now perfectly oriented to face forward along the curve, banking and turning realistically as they follow the path.