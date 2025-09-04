**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Shader

**Core Function:** Simulates the unique way light scatters and reflects off of cylindrical hair strands, creating realistic highlights and translucency.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **Component:** The most important setting, defining which physical light interaction is being calculated.
    
    - **Reflection:** Simulates the primary highlight, the sharp "sheen" of light bouncing off the outer surface (cuticle) of the hair.
        
    - **Transmission:** Simulates the secondary, softer glow of light that passes through the semi-transparent hair strand and exits on the other side.
        
- **Color (Input):** Defines the base color of the hair strand.
    
- **Roughness U/V (Input):** A pair of values controlling highlight sharpness. U controls the spread along the hair's length, while V controls the spread across its width.
    
- **Offset (Input):** Shifts the position of the highlight along the strand, which can be used to simulate different hair types or a "wet" look.
    

**Practical Application:**  
This node is specifically designed to create realistic hair. Using a simple Glossy or Diffuse shader on hair curves results in a fake, "plastic tube" look. Real hair has a complex interplay between a sharp outer highlight and a soft internal glow.

The problem is how to create both of these effects simultaneously. The Hair BSDF node is the solution, but its power is fully unlocked by using it twice.

1. To build a complete hair material, add two Hair BSDF nodes.
    
2. Set the first node's Component to Reflection. This node will create the sharp, primary highlight. You might give it a low Roughness U value for a defined sheen and a white Color to simulate a clean cuticle reflection.
    
3. Set the second node's Component to Transmission. This node will create the softer, colored light that passes through the hair. Use the hair's actual Color here (e.g., brown) and a slightly higher Roughness U for a softer falloff.
    
4. Combine these two nodes using an Add Shader.
    
5. The result is a far more realistic material. The Reflection component provides the sharp, whitish "sheen" that defines the hair's shape, while the Transmission component adds the soft, colored under-glow that gives it volume and depth, perfectly simulating the complex look of real hair.