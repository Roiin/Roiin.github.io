**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Color

**Core Function:** Inverts the input color or texture, turning bright areas dark, dark areas bright, and flipping colors to their complementary hue.

**Key Properties & Settings:**

- **Color (Output):** The final, inverted color.
    
- **Color (Input):** The socket for the source color or texture to be inverted.
    
- **Fac (Input):** A factor to control the strength of the inversion. A value of 0.0 has no effect, 0.5 results in a flat 50% gray, and 1.0 applies a full, 100% inversion.
    

**Practical Application:**  
This node's most common and powerful use is to flip the behavior of a grayscale mask. Imagine you are using the Ambient Occlusion node to add procedural dirt to the crevices of an object. The AO node outputs a mask that is black in the crevices and white on the exposed surfaces.

The problem is that to use this with a Mix Shader, you typically need a mask where the effect area is white. If you plug the raw AO mask into the Fac, the dirt will appear on the exposed surfaces, not in the crevices. You need to invert the mask. The Invert node is the simplest and most direct solution.

1. Start with your Ambient Occlusion node.
    
2. Connect its AO (grayscale) output to the Color input of an Invert node. The output of the Invert node will now be a mask that is white in the crevices and black everywhere else.
    
3. Create two shaders: one for your clean base material and one for the "Dirt" material.
    
4. Use a Mix Shader to combine them, with the clean material in the top slot and the dirt in the bottom.
    
5. Connect the output of the Invert node to the Fac input of the Mix Shader.
    
6. The result is a perfectly applied dirt effect. The inverted (now white) areas correctly reveal the dirt shader in the crevices and corners, demonstrating how a simple inversion can completely reverse the logic of a mask to achieve the desired outcome.