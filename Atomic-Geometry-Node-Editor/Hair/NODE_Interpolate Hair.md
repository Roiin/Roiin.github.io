**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Generation)

**Core Function:** Generates a new, dense set of hair curves by interpolating the shape and attributes of a sparse set of existing guide curves.

**Key Properties & Settings:**

- **Geometry (Input):** The sparse set of "guide" hair curves that will be interpolated.
    
- **Surface (Input):** The mesh geometry on which the new hair will be generated.
    
- - **Surface UV Map (Input):** The UV map of the surface mesh, used for distributing the new curves.
        
- **Density (Input):** The number of new hair curves to generate per unit of surface area.
    
- **Density Mask (Input):** A float field used to control where the new hairs are generated, similar to the Generate Hair Curves node.
    
- **Distance to Guides (Input):** Defines the maximum distance from a guide curve that a new interpolated hair can be spawned. This helps create natural clumping and parting.
    
- **Guide Index (Output):** An integer field that stores which of the original guide curves was the primary influence for each new interpolated hair.
    

**Practical Application:**  
This node is an alternative to Duplicate Hair Curves for creating density. While Duplicate simply creates copies in a radius, Interpolate creates new hairs on the surface and blends the shapes of nearby guides to determine their form. This is excellent for creating hairstyles with soft, natural blending between different groomed sections.

- **The Goal:** To create a full, dense head of hair for a character that blends smoothly from the longer hair on top to the shorter, combed hair on the sides.
    
- - **The Problem:** You have groomed two different sets of sparse guide curves: long ones on top and short ones on the sides. If you simply use Duplicate Hair Curves, you will get two distinct clumps with a harsh transition. You need a method that can create new hairs between these regions and smoothly blend their shapes.
        
- **The Solution:** Use Interpolate Hair Curves to fill in the density.
    
    1. Join your two sets of groomed guide hairs (long top, short sides) into a single geometry. Connect this to the Geometry input.
        
    2. Connect the character's scalp mesh to the Surface input and specify its UV map.
        
    3. Set the Density to a high value to create a thick head of hair.
        
    4. The node will now generate new hairs across the entire scalp. For each new hair, it will look at the nearby guide curves. A hair generated on the top of the head will be influenced by the long guides and will become long. A hair on the sides will be influenced by the short guides and will become short. A hair at the transition point will be influenced by both, and its shape and length will be a smooth average of the two.
        
    5. The Guide Index output can be used later to add subtle clumping back towards the original guides.
        

This method produces a very soft and natural-looking result, creating a cohesive hairstyle that appears to have been groomed as a single piece, rather than assembled from distinct parts.