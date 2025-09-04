**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a procedural cellular pattern by scattering points in space and then calculating values based on the distance between them, creating effects ranging from organic cells to crystalline structures and crack maps.

**Key Properties & Settings:**

- **Outputs:**
    
    - **Distance:** The most common output. It provides a grayscale gradient from the center of each cell outwards.
        
    - **Color:** Assigns a unique, random solid color to each individual cell.
        
    - **Position:** Outputs the coordinates of the center point of each cell.
        
- **Feature (Property):** The most critical setting, as it completely changes what the node calculates.
    
    - **F1:** The default mode, calculates the distance to the single closest point.
        
    - **Distance to Edge:** A highly powerful mode that calculates the distance to the boundary between cells, creating a perfect network of lines.
        
- **Distance Metric (Property):** Determines the shape of the cells. Euclidean (the default) creates rounded cells. Manhattan creates diamond/square shapes, and Chebychev creates perfect squares.
    
- **Randomness (Input):** Controls the distribution of the points. A value of 0 creates a perfect, repeating grid, while a value of 1.0 creates a completely chaotic, organic pattern.
    
- **Scale (Input):** Controls the overall size and density of the cells.
    

**Practical Application:**  
The Voronoi node's Distance to Edge feature is the definitive solution for creating procedural cracks. Imagine you are building a material for a frozen lake or a block of old **ice**.

The problem is that a simple noise texture can create a bumpy surface, but it cannot generate the sharp, interconnected network of cracks that forms when ice freezes and stresses. You need a pattern that looks like a fractured web. The Voronoi node is the perfect tool for this.

1. Start with your base ice material, likely a Principled BSDF with high Transmission.
    
2. Add a Voronoi Texture node and, critically, change its Feature property from F1 to Distance to Edge.
    
3. The Distance output of the node will now be a grayscale map where the edges between the cells are black, fading to white in the center of the cells.
    
4. To isolate just the cracks, connect this Distance output to a ColorRamp node. Invert the ramp (slide the white handle to the left and the black handle to the right) and move the white handle very close to the left side. This will "crush" the gradient into a sharp, white network of cracks on a black background.
    
5. This crack mask can now be used in multiple ways. You can plug it into the Height of a Bump node to make the cracks appear recessed. You can also use it as the Fac for a Mix Shader to blend your clear ice with a rougher, more opaque "cracked ice" shader. The result is a highly realistic and art-directable network of cracks that would be impossible to achieve with standard noise textures.