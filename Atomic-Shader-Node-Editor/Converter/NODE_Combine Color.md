**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Constructs a single color output from separate, individual input channels based on a chosen color model (RGB, HSV, or HSL).

**Key Properties & Settings:**

- **Color (Output):** The final, combined color.
    
- **Mode (Property):** The core control that determines which input channels are available.
    
    - **RGB:** Provides Red, Green, and Blue inputs. This is the most direct and common way to build a color.
        
    - **HSV:** Provides Hue, Saturation, and Value inputs. This is more artist-friendly, allowing you to construct a color based on its position on the color wheel, its intensity, and its brightness.
        
- **Alpha (Input):** An optional grayscale input to define the transparency of the final combined color.
    

**Practical Application:**  
This node is the counterpart to the Separate Color node and is essential when you need to manipulate individual color channels before reassembling them. It's particularly useful for creating complex procedural effects or for packing different grayscale masks into a single color texture.

Imagine you are creating a stylized sci-fi material and you want the red channel of the color to pulse with one noise pattern, while the blue channel glows with a different, slower pattern.

The problem is that a single texture can't easily contain two independent, animated effects. You need to build the final color from separate, moving parts. The Combine Color node is the solution.

1. Add a Combine Color node and leave its Mode set to RGB.
    
2. Create your first procedural effect for the red channel: use a Noise Texture with a Mapping node animated to move it quickly. Connect this texture to the R (Red) input of the Combine Color node.
    
3. Create a second effect for the blue channel: use another Noise Texture, but animate its Mapping node to move much more slowly. Connect this one to the B (Blue) input.
    
4. You can leave the G (Green) input empty (or set it to 0) for a purely red-and-blue pulsing effect.
    
5. Connect the Color output of the Combine Color node to the Emission Color of a Principled BSDF.
    
6. The result is a dynamic material with independent effects packed into its color channels. The red components will shimmer and move quickly, while the blue components will undulate slowly, creating a complex, layered effect that would be difficult to manage without being able to build the final color from separate, procedurally generated inputs.