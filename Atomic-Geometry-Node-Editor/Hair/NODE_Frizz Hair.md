**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Adds small-scale, random offsets to the points along each hair curve, creating a chaotic, "frizzy" effect that breaks up uniformity.

**Key Properties & Settings:**

- **Factor (Input):** A global multiplier for the overall strength of the frizz effect.
    
- **Distance (Input):** Controls the maximum magnitude of the random offsets applied to the curve points.
    
- **Shape (Input):** A falloff curve that controls the frizz strength along the length of each hair, from root to tip. This is often used to make the tips frizzier than the roots.
    
- **Seed (Input):** An integer used to generate a different random frizz pattern.
    
- **Cumulative Offset (Input):** When enabled, the offset of each point is added to the offset of the next point along the curve, creating a more tangled, meandering frizz instead of just local noise.
    
- **Preserve Length (Input):** When enabled, this ensures that the hair strands do not get longer as a result of the frizz deformation.
    

**Practical Application:**  
This node is essential for adding a final layer of natural imperfection to fur and hair. After the main grooming is done, a coat of fur on an animal might look too perfect and smooth, like a carpet. The Frizz Hair Curves node breaks up this digital perfection.

- **The Goal:** To make the short, coarse coat of fur on a rhino look more realistic by adding subtle, chaotic imperfections.
    
- **The Problem:** Procedurally generated hairs are often perfectly parallel to each other, which looks unnatural. Real fur has countless small variations, bends, and kinks.
    
- **The Solution:** Apply a Frizz Hair Curves node as one of the last steps in the grooming process.
    
    1. After generating and combing the main direction of the rhino's fur, add the Frizz Hair Curves node.
        
    2. Use a very small Distance value, as rhino fur is stiff and short; you want to create subtle noise, not large curls.
        
    3. Adjust the Shape so that the frizz is minimal at the root and slightly stronger at the tip of each hair.
        
    4. The Seed can be randomized to get a pleasing pattern of chaos.
        

This introduces fine, random kinks along each hair strand, breaking up the smooth, parallel lines and specular highlights. The result is a much more believable and organic-looking coat that appears less like a computer-generated surface and more like real animal fur.