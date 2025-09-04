**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Shader

**Core Function:** An advanced, all-in-one, physically-based shader designed to realistically simulate the complex way light interacts with hair and fur.

**Key Properties & Settings:**

- **Color Parametrization (Property):** The most important setting, which changes the node's inputs.
    
    - **Melanin Concentration:** The preferred, physically-based mode. Instead of picking an arbitrary color, you control the amount and type of natural pigments.
        
    - **Direct Coloring:** A simpler, artist-driven mode where you just pick the final RGB color you want.
        
- **Melanin Controls (when in Melanin mode):**
    
    - **Melanin:** Controls the quantity of pigment, effectively the darkness of the hair. A low value is white/blonde, a high value is dark brown/black.
        
    - **Melanin Redness:** Controls the type of pigment, blending between eumelanin (brown/black) and pheomelanin (red/orange). This is the control for creating red or auburn hair.
        
    - **Tint:** A simple color input that acts like a dye, applied on top of the natural melanin color.
        
- **Physical Properties:**
    
    - **Roughness:** Controls the sharpness of the primary highlight along the length of the hair strand.
        
    - **Radial Roughness:** Controls the spread of the highlight across the width of the hair strand.
        
- **Variation Controls:**
    
    - **Random Color:** Varies the Melanin value for each individual hair strand, which is crucial for breaking up uniformity and achieving a natural look.
        
    - **Random Roughness:** Varies the Roughness values for each individual strand.
        
    - **Random (Input):** The socket where a per-strand random number (usually from a Curves Info node) should be connected to drive the randomization.
        

**Practical Application:**  
This node is essential for any character or creature that requires realistic hair or fur. Using a standard shader on hair curves makes them look like plastic tubes. Natural hair is never perfectly uniform; every strand has slight variations in color and texture.

The problem is how to procedurally create this subtle, lifelike variation without making thousands of different materials. The Principled Hair BSDF is the solution.

1. Start with the Principled Hair BSDF and set its Color Parametrization to the powerful Melanin Concentration mode.
    
2. To create a natural brown hair color, set the Melanin to a medium value (e.g., 0.5) and Melanin Redness to a value around 1.0. This combination simulates a natural balance of pigments.
    
3. The most important step is to break up the "perfect CG" look. Increase the Random Color slider to a small value, like 0.2. This tells the shader that each strand's melanin level can be 20% lighter or darker than the base value.
    
4. For maximum effect, add a Curves Info node and connect its Random output to the Random input of the Principled Hair BSDF. This provides a unique seed value for every single strand of hair.
    
5. The result is a transformation from a flat, uniform wig to a natural head of hair. Each strand now has a subtly unique shade, catching the light in a slightly different way. This randomization is the key to bridging the gap from a synthetic look to a believable, organic result.