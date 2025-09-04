**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Averages the shape of each hair curve with its neighbors within a defined radius, resulting in a smoother, more uniform, and less noisy appearance.

**Key Properties & Settings:**

- **Factor (Input):** A global control for the strength of the blending effect. A factor of 0 has no effect, while 1.0 applies the full blend.
    
- **Blend Radius (Input):** Defines the search distance around each curve's points to find neighbors for blending.
    
- **Blend Neighbors (Input):** Sets the maximum number of nearby curves that will be averaged together to create the new shape.
    
- **Preserve Length (Input):** When enabled, this ensures that the hair strands maintain their original length during the blending process, preventing unwanted shrinking or stretching.
    

**Practical Application:**  
This node is excellent for grooming and cleaning up a hairstyle, acting like a smoothing brush to tame stray hairs. Imagine you are creating the fur for a zebra, and after applying some initial noise and frizz effects, the coat looks too messy and chaotic, with individual hairs sticking out unnaturally.

- **The Goal:** To give the zebra's coat a more cohesive and sleek appearance by making the hairs lie more consistently with their neighbors, without losing the overall grooming direction.
    
- **The Problem:** Randomizing effects can create "flyaway" hairs that break the silhouette and make the fur look unkempt. You need a way to average out these local inconsistencies.
    
- **The Solution:** The Blend Hair Curves node can be applied as a final grooming step.
    
    1. Place the node after other deformation nodes like Hair Curves Noise or Frizz Hair Curves.
        
    2. Set a relatively small Blend Radius to ensure you are only blending immediately adjacent hairs.
        
    3. Use a low number for Blend Neighbors (e.g., 3 to 5) to average out the most extreme stray hairs without flattening the entire hairstyle.
        
    4. The Factor can then be used to dial in the desired amount of smoothing.
        

By blending the shape of each hair with its local neighborhood, the node pulls in the outliers and reduces the visual noise. This results in a much cleaner, more natural-looking coat for the zebra, where the fur flows together smoothly.