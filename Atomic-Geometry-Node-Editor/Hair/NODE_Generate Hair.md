**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Generation)

**Core Function:** Creates a new set of hair curves from scratch on a target surface mesh, using a UV map and density controls to determine their placement.

**Key Properties & Settings:**

- **Surface (Input):** The mesh geometry on which the hair will be generated. This is a mandatory input.
    
- - **Surface UV Map (Input):** The UV map of the surface mesh used for hair placement. This is a mandatory input and is critical for using texture-based masks.
        
- **Density (Input):** The number of hair curves to generate per unit of surface area.
    
- **Density Mask (Input):** A float field (like a vertex group) used to multiply the Density, providing artistic control over where hair grows. A value of 0 in the mask means no hair will grow.
    
- **Mask Texture (Input):** An image texture that can be used as a mask to discard generated hairs, offering another layer of artistic control.
    
- **Hair Length (Input):** A field that defines the length of the newly generated hair curves.
    
- **Poisson Disk Distribution (Input):** When enabled, this prevents hairs from spawning too close to each other, resulting in a more even and natural-looking distribution.
    
- **Seed (Input):** An integer for randomizing the hair placement.
    

**Practical Application:**  
This node is the starting point for nearly all procedural hair systems. It is used to create the initial, sparse set of "guide hairs" that define the overall hairstyle. For example, when creating the fur for a zebra, you must first define where the fur should grow and its base length.

- **The Goal:** To generate the initial coat of fur on a zebra, ensuring that hair grows on its main body but not on its hooves or the inside of its mouth, and that the hair of the mane is longer than the body fur.
    
- **The Problem:** You need precise control over the placement and length of the initial hairs. Simply scattering hairs uniformly over the entire model is incorrect and inefficient.
    
- **The Solution:** Use the Generate Hair Curves node with masks to control density and length.
    
    1. The zebra model must have a UV map. Connect the zebra geometry to the Surface input and specify the UV Map.
        
    2. Create a vertex group on the zebra model, painting a weight of 1.0 where fur should grow and 0.0 on areas like the hooves. Connect this attribute to the Density Mask input. This will prevent any hair from spawning in the zero-weight areas.
        
    3. Create a second vertex group or texture to define length. Paint a high value along the spine for the mane and a lower value for the body fur. Connect this map to the Hair Length input.
        
    4. Set a relatively low Density value. The goal is to create a sparse set of guide hairs that can be efficiently groomed, not the final dense coat.
        
    5. Enable Poisson Disk Distribution to ensure the guide hairs are spaced evenly.
        

The output is a clean, art-directable set of guide curves. They exist only where you painted the density mask and their lengths are controlled by your length map. This provides a perfect, performance-friendly foundation for all subsequent grooming steps like duplicating, clumping, and frizzing.