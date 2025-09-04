**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Utility)

**Core Function:** Re-spaces the existing control points along each curve to be evenly distributed, without changing the curve's overall shape.

**Key Properties & Settings:**

- **Curves (Input):** The hair curve geometry to be processed.
    
- **Factor (Input):** A global multiplier for the strength of the effect. At 1.0, the points are perfectly evenly spaced; at 0.0, they are unchanged.
    
- **Feature Awareness (Input):** When enabled, this option attempts to preserve sharp corners and details in the curve by placing more points in areas of high curvature.
    

**Practical Application:**  
This node is a utility used to improve the quality of deformation on curves that have a poor or uneven distribution of control points. Imagine you have a set of hair curves that you want to deform with a Hair Curves Noise node to make them wavy.

- **The Goal:** To ensure that a noise deformation applied to a set of hair curves results in a smooth, high-quality wave pattern.
    
- **The Problem:** The hair curves were generated with very few control points, and these points are clustered near the root. The long segment towards the tip has only two points. When you apply a noise deformer, the root section will show the wave, but the long tip segment will remain a perfectly straight line, creating an ugly, low-resolution artifact. You need more, evenly spaced points to capture the detail of the noise.
    
- **The Solution:** Use Redistribute Curve Points before the deformation.
    
    1. First, you need to add more points. Use a Subdivide Curve node to increase the overall point count. However, this may still result in an uneven distribution.
        
    2. Add a Redistribute Curve Points node after the subdivision.
        
    3. Set the Factor to 1.0. The node will take all the existing points on each curve and slide them along the curve's length until they are all an equal distance apart.
        
    4. Now, place your Hair Curves Noise node after the redistribution.
        

Because the curves now have a high-resolution and evenly spaced set of control points, the noise deformer has the necessary geometry to work with. The resulting wave pattern will be smooth and detailed along the entire length of the hair, with no more low-resolution artifacts.