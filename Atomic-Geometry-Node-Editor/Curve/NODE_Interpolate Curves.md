- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Generates a dense set of new "child" curves by intelligently interpolating the shape, length, and attributes of a few existing "guide" curves. This is the primary method for creating high-density hair and fur that is still easy to art-direct.
    
- **Key Properties & Settings:**
    
    - **Guide Curves (Socket - Input):** The sparse, artist-controlled curves that define the main hairstyle or fur flow.
        
    - **Guide Up (Socket - Input):** An "up" vector (usually the surface normal of the scalp/skin) for each guide curve's root. This helps the interpolation respect the surface curvature.
        
    - **Guide Group ID (Socket - Input):** An integer ID to separate guides into groups (e.g., 'bangs', 'sideburns'). Interpolation will only happen between guides within the same group.
        
    - **Points (Socket - Input):** A point cloud representing the root positions of the new 'child' curves to be generated.
        
    - **Max Neighbors (Socket - Input):** The maximum number of nearby guide curves to consider when interpolating a new curve. Lower numbers are faster; higher numbers can produce smoother results.
        
    - **Curves (Socket - Output):** The final, high-density set of curves, containing both the original guides and the newly generated children.
        
    - **Closest Index (Socket - Output):** For each new child curve, this outputs the index of the most influential guide curve. This is crucial for transferring attributes.
        
- **Practical Application:** This node is essential for creating a full, dense mane for a lion.
    
    1. **The Problem:** It is impossible to manually style the tens of thousands of individual hairs required for a realistic lion's mane.
        
    2. **The Solution:**
        
        - First, the artist styles only a few hundred "guide" curves by hand, defining the overall shape, length, and clumping of the mane. This is a manageable and creative process.
            
        - Next, use Distribute Points on Faces on the lion's scalp mesh to generate 50,000 points where the final hairs should grow.
            
        - Use the Interpolate Curves node. The hand-styled curves are the Guide Curves, and the 50,000 generated points are the Points. You provide the scalp's Normal for the Guide Up and Points Up inputs.
            
        - The node then generates a new curve at each of the 50,000 points, perfectly blending the shapes of the nearest guide curves.
            
    3. **The Result:** A full, dense, and realistic mane that perfectly follows the artist's original styling, but with a level of detail that would be impossible to create manually. You can even transfer attributes: if the artist makes one guide curve grey, you can use the Closest Index output to find all the child hairs influenced by it and make them grey as well.