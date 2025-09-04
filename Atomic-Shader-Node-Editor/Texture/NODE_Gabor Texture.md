**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a procedural noise pattern characterized by random, flowing bands, offering precise control over their direction and frequency.

**Key Properties & Settings:**

- **Phase (Output):** The most powerful output for structured patterns. It provides the clean, wavy line pattern of the noise without the random brightness variations, making it ideal for creating ridges or grain.
    
- **Anisotropy (Input):** The master control for directionality. A value of 1.0 creates perfectly parallel, directional bands. A value of 0 creates omnidirectional noise similar to a standard Noise Texture.
    
- **Orientation (Input):** Sets the angle or direction of the directional bands, simulating a "flow" direction.
    
- **Frequency (Input):** Controls the density or tightness of the bands, determining how many bands appear within a given area.
    
- **Type (Property):** Switches the calculation between 2D and 3D. 2D is faster and suitable for most surface work, while 3D creates a pattern that is consistent through the volume of an object.
    

**Practical Application:**  
This node's unique, directional nature makes it perfect for creating procedural textures with a distinct flow, such as wind-swept sand dunes or certain types of biological patterns.

The problem with creating a convincing sand dune material is that a standard Noise Texture is too chaotic and random. It creates blobs, not the parallel, flowing ridges formed by wind. You need a texture that has an inherent, controllable directionality. The Gabor Texture node is the ideal solution.

1. Start with a Principled BSDF for your sand material.
    
2. Add a Gabor Texture node. To create the dune ridges, we will use it to drive a Bump map.
    
3. Set the Anisotropy to a high value, like 0.9, to make the bands strongly directional.
    
4. Use the Orientation value to set the direction of your "wind," which will define the angle of the dunes.
    
5. Adjust the Scale and Frequency to control the size and spacing of the dune ridges.
    
6. Crucially, connect the Phase output of the Gabor node to the Height input of a Bump node. The Phase output provides clean, smooth waves perfect for this effect.
    
7. Connect the Bump node's Normal output to the Principled BSDF's Normal input.
    
8. The result is a highly realistic and art-directable sand dune surface, where the ridges flow in a natural, parallel pattern that would be impossible to achieve with a standard noise texture.