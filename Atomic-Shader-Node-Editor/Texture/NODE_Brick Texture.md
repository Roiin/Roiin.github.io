**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Procedurally generates a customizable pattern of bricks and the mortar that separates them.

**Key Properties & Settings:**

- **Color (Output):** The primary color output, showing the complete pattern with bricks and mortar colored as specified.
    
- **Factor (Output):** A powerful grayscale mask where the mortar is white and the bricks are black. This is essential for treating the brick and mortar surfaces differently.
    
- **Color 1 / Color 2:** The two main colors for the bricks. The Bias setting controls the blend between them, allowing for natural color variation.
    
- **Mortar:** Sets the color of the gaps between the bricks.
    
- **Scale:** Controls the overall size of the entire brick pattern.
    
- **Mortar Size:** Defines the thickness of the mortar lines.
    
- **Brick Width / Row Height:** Controls the aspect ratio and dimensions of the individual bricks.
    
- **Offset:** Sets the classic "running bond" pattern, offsetting alternating rows of bricks.
    

**Practical Application:**  
This node is the foundation for creating realistic, procedural brick wall materials. The primary problem with a simple brick image texture is that it's flat—the bricks and the mortar have the identical roughness and height, which looks fake. Real mortar is typically rougher and slightly recessed.

The Brick Texture node is the solution because it provides a Factor output that allows you to isolate the mortar for separate treatment.

1. Start with a Principled BSDF. Connect the Color output of the Brick Texture to the Base Color input to get the visual pattern.
    
2. To give the mortar a different surface quality, connect the Factor output to the Fac of a Mix Color node. Use this to blend two different roughness values—a lower value for the bricks and a higher value for the rougher mortar—and plug the result into the Roughness input of the Principled BSDF.
    
3. To create physical depth, connect the Factor output directly to the Height input of a Bump node, and then connect the Bump node's Normal output to the Principled BSDF's Normal input. This will make the mortar (the white part of the mask) appear recessed below the surface of the bricks.
    
4. The result is a convincing, three-dimensional brick wall material where the bricks and mortar not only have different colors, but different physical properties, all controlled procedurally.