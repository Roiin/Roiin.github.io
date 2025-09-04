**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** A versatile node that blends between two inputs of the same data type (Float, Vector, or Color) using a factor to control the interpolation.

**Key Properties & Settings:**

- **Result (Output):** The final, blended output. Its data type matches the selected Data Type.
    
- **Data Type (Property):** The core control that changes the node's function and the type of its input/output sockets.
    
    - **Float:** Blends between two single numerical values (gray sockets).
        
    - **Vector:** Blends between two vectors (purple sockets).
        
    - **Color:** Blends between two colors (yellow sockets), gaining access to numerous advanced blend modes. This mode is identical to the Mix Color node.
        
- **Fac (Input):** The factor that controls the mix. A value of 0.0 uses only input A, 1.0 uses only input B, and grayscale values blend between them.
    
- **A / B (Inputs):** The two data inputs to be blended.
    

**Practical Application:**  
While the Color mode is the most feature-rich, the Float and Vector modes are essential utilities for blending non-color data. The Float mode is perfect for creating materials with variable surface properties, like a surface that is a mix of smooth and rough areas.

Imagine you are creating a material for a partially polished piece of metal where some areas have been scuffed up. You have a Noise Texture to act as a mask for the scuffed parts.

The problem is how to blend between a "polished" roughness value (e.g., 0.1) and a "scuffed" roughness value (e.g., 0.6). The Mix node in Float mode is the solution.

1. Add a Mix node and set its Data Type to Float. The sockets will turn from yellow to gray.
    
2. In the A input, enter the value for your polished areas: 0.1.
    
3. In the B input, enter the value for your scuffed areas: 0.6.
    
4. Take your Noise Texture (processed through a ColorRamp to create a high-contrast mask) and plug it into the Fac input.
    
5. Connect the Result output of the Mix node to the Roughness input of your Principled BSDF.
    
6. The result is a material with perfectly controlled roughness. The areas of the mask that are black will use the A value (0.1, polished), and the areas that are white will use the B value (0.6, scuffed). This allows you to blend any two numerical properties (like Roughness, Metallic, IOR, etc.) using a texture, which is a fundamental technique for creating complex, layered materials.