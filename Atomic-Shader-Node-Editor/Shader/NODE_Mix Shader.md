**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Selectively blends between two different shader nodes using a grayscale mask or a numerical value as the controller.

**Key Properties & Settings:**

- **Shader (Output):** The final, mixed shader result.
    
- **Fac (Input):** The "Factor" or controller for the mix. It reads a grayscale input: a value of 0.0 (black) will exclusively use the top shader input, a value of 1.0 (white) will exclusively use the bottom shader input, and gray values will create a smooth blend between the two.
    
- **Shader (Inputs):** The two green sockets where the shaders to be mixed are connected. The top socket corresponds to a Fac value of 0.0, and the bottom socket corresponds to 1.0.
    

**Practical Application:**  
This node is one of the most fundamental tools for creating complex materials with multiple layers. It is the primary method for combining different surface types, such as paint and **rust**.

Imagine you are creating a material for an old, weathered metal barrel. The barrel was originally painted blue, but over time, the paint has chipped and worn away, revealing the rough rust underneath.

The problem is that you have two distinct material ideas—"Blue Paint" and "Rust"—but you need them to exist on the same surface, with one realistically giving way to the other. The Mix Shader is the solution.

1. Create two separate Principled BSDF shaders. Configure the first to look like glossy blue paint and the second to look like rough, orange rust.
    
2. Add a Mix Shader node. Connect the "Blue Paint" shader to the top input and the "Rust" shader to the bottom input.
    
3. To create the chipping effect, add a Noise Texture and connect it through a ColorRamp node. Adjust the ColorRamp to create a high-contrast, black-and-white pattern. This pattern will serve as your wear-and-tear mask.
    
4. Connect the output of this ColorRamp to the Fac input of the Mix Shader.
    
5. The result is a perfect layered material. In the areas where the noise mask is black, the "Blue Paint" shader appears. In the areas where the mask is white, the "Rust" shader is revealed, creating a completely procedural and art-directable wear effect.