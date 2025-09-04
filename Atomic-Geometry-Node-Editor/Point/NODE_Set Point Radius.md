- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Point
    
- **Core Function:** Sets the radius attribute for each point in a point cloud. This attribute primarily controls the visual size of the points in the 3D Viewport and can also be used as a general-purpose float attribute for other procedural operations.
    
- **Key Properties & Settings:**
    
    - **Points (Socket - Input):** The source point cloud geometry.
        
    - **Selection (Socket - Input):** A Boolean mask. The radius will only be set on points where this is True.
        
    - **Radius (Socket - Input):** A float field that provides the new radius value for each selected point.
        
    - **Points (Socket - Output):** The point cloud with the updated radius attribute.
        
- **Practical Application:** This node is essential for procedurally controlling the Radius attribute, which is then often used to control the scale of instances. Imagine you are creating a magical animal that is dissolving into a cloud of particles, and you want the particles to shrink over time before disappearing.
    
    1. Start with a point cloud that represents your animal.
        
    2. **The Goal:** To animate the radius of all points from their current size down to zero over the course of the animation.
        
    3. Use the Set Point Radius node.
        
    4. You need an animated value for the Radius input. Use a Scene Time node and feed its Frames or Seconds output into a Map Range node.
        
    5. Configure the Map Range node to map your animation duration (e.g., from frame 100 to frame 150) to a Radius range (from 1.0 down to 0.0). This creates a shrinking effect.
        
    6. To make the effect more interesting, you can multiply this animated value by a Noise Texture. This will cause the points to shrink at slightly different rates, making the dissolution effect less uniform and more organic.
        
    7. The final result is a point cloud where each point's radius animates from its initial size down to zero. If you were to instance geometry on these points and use the Radius attribute to drive their scale, you would have a perfect "dissolve" animation.