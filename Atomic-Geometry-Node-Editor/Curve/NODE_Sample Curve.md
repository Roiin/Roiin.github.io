- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Sample)
    
- **Core Function:** Acts as a precise "tape measure" for curves. It finds a single point along a curve at a specific distance (defined by a Length or a 0-1 Factor) and outputs detailed information about the curve at that exact location, such as its Position, Tangent, and Normal.
    
- **Key Properties & Settings:**
    
    - **Curves (Socket - Input):** The source curve to be sampled.
        
    - **Value (Socket - Input):** An optional field to sample a custom attribute from the curve (like Radius or Tilt) at the specified point.
        
    - **Mode (Property):**
        
        - **Factor:** The sample location is determined by a 0-to-1 percentage of the curve's total length.
            
        - **Length:** The sample location is determined by an absolute distance from the start of the curve.
            
    - **Curve Index (Socket - Input):** Allows you to specify which spline to sample from in a multi-spline object.
        
    - **Position (Socket - Output):** The exact location of the sampled point in 3D space.
        
    - **Tangent (Socket - Output):** The forward direction of the curve at the sampled point.
        
    - **Normal (Socket - Output):** The "up" direction of the curve at the sampled point.
        
- **Practical Application:** This node is perfect for creating complex constructions that are anchored to a base curve. Imagine procedurally creating a spider web between two points.
    
    1. First, you create the main radial support strands of the web using a Star curve primitive.
        
    2. **The Goal:** You now need to create the spiral threads that connect these radial strands.
        
    3. Use a Duplicate Elements node on the star curve to create multiple copies of it, one for each ring of the spiral.
        
    4. To create the spiral, you need to scale each of these duplicated stars. Use the Duplicate Index to control the Scale in a Transform Geometry node, making each star progressively smaller than the last. Now you have the concentric rings.
        
    5. Use a Resample Curve node on these concentric star rings to create the points where the spiral will connect.
        
    6. **The Key Step:** Use the Sample Curve node. The Curves input is your original set of radial strands. The Sample Position is the position of each point on your concentric rings. The Sample Curve node will find, for each point on the rings, the closest point on the radial strands.
        
    7. The Position output of the Sample Curve node now gives you a new set of points that are perfectly snapped to the radial strands. You can use these points, along with the original ring points, to create the individual lines of the spiral web, ensuring a perfect connection.