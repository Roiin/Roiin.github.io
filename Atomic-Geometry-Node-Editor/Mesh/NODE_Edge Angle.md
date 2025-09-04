- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each edge in a mesh, this node calculates the angle between the two faces that share it, distinguishing between convex (outward) and concave (inward) angles.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Unsigned Angle (Socket - Output):** The absolute angle of the edge, from 0 (flat) to PI (180 degrees). Useful for measuring the general "sharpness" of a corner.
        
    - **Signed Angle (Socket - Output):** The angle with a sign. Negative values indicate convex (outward-pointing) edges, while positive values indicate concave (inward-pointing) edges. This is essential for distinguishing between ridges and crevices.
        
- **Practical Application:** This node is fundamental for creating procedural weathering and wear-and-tear effects, for example, adding scraped paint to the exposed edges of a piece of armor.
    
    1. **The Goal:** You want to create a material that automatically reveals bare metal on the sharpest, most exposed edges of a painted suit of armor.
        
    2. **The Problem:** You need a way to procedurally identify only the sharp, outward-facing edges where damage would naturally occur.
        
    3. **The Solution:**
        
        - Use the Edge Angle node on your armor mesh. The Signed Angle output is perfect for this.
            
        - Use a Compare node to check where the Signed Angle is less than a certain negative value (e.g., -0.5). This creates a boolean selection that is True only for the sharp, convex edges.
            
        - Use a Store Named Attribute node to save this boolean mask to the geometry, naming it "edge_wear".
            
        - In the Shader Editor for the armor's material, add an Attribute node and type in "edge_wear".
            
        - Use this attribute as the factor in a Mix Shader to blend between your main 'Painted Metal' shader and a secondary 'Scratched Bare Metal' shader.
            
    4. The result is a highly realistic weathering effect. Paint is automatically "scraped off" on all the sharp edges, and the effect will intelligently update if you ever change the armor's shape.