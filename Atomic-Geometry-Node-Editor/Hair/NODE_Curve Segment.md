**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Read)

**Core Function:** Provides information about the line segment immediately preceding each control point on a curve.

**Key Properties & Settings:**

- **Segment Length (Output):** A float value for each point, representing the length of the segment connecting it to the previous point on the curve.
    
- **Segment Direction (Output):** A vector for each point, representing the direction from the previous point to the current one.
    
- **Neighbor Index (Output):-** The index of the previous control point on the curve.
    

**Practical Application:**  
This node is useful for creating effects that depend on the local orientation of a curve. A great example is instancing thorns on a winding vine, where each thorn needs to point perpendicularly outwards from its local segment.

- **The Goal:** To place thorns on a procedural vine so that each thorn is oriented correctly, pointing away from the curve at that specific point.
    
- **The Problem:** The vine is a complex, twisting curve. A simple Align Rotation to Vector using the curve's overall Normal might not be accurate enough for the local twists and turns. You need the precise direction of the curve at every point where a thorn will be placed.
    
- **The Solution:** The Curve Segment node provides the local direction (the tangent) needed to calculate the thorn's orientation.
    
    1. Start with your procedural vine curve. Use a Resample Curve node to create the points where thorns will be instanced.
        
    2. Use a Curve Segment node. The Segment Direction output is the tangent vector at each of those points.
        
    3. You need a direction that is perpendicular to this tangent. You can get this by calculating the Cross Product (using a Vector Math node) between the Segment Direction and another arbitrary vector (like the curve's main Normal). This gives you a direction pointing outwards from the vine.
        
    4. To add variation, you can rotate this "outward" vector around the Segment Direction axis by a random amount. Use a Vector Rotate node with Segment Direction as the Axis and a Random Value as the Angle.
        
    5. Feed this final, randomized outward vector into an Align Rotation to Vector node to create the orientation for your instanced thorn models.
        

This ensures that each thorn is perfectly aligned to the local curvature of the vine, pointing outwards in a natural and believable way.