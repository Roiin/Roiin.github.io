**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Performs a wide variety of mathematical operations on numerical (float) values.

**Key Properties & Settings:**

- **Value (Output):** The numerical result of the operation.
    
- **Operation (Property):** A large dropdown menu that selects the function to be performed. The node's inputs will dynamically change to match the selected operation.
    
- **Common Operations:**
    
    - **Basic Arithmetic:** Add, Subtract, Multiply, Divide. These are the most frequently used functions for simple adjustments.
        
    - **Comparison:** Greater Than and Less Than. These are extremely powerful for creating masks. They take two inputs and output a hard black (0.0) or white (1.0) value based on the comparison.
        
    - **Rounding:** Round, Floor, Ceil. Used to snap continuous values to whole numbers.
        
    - **Trigonometric:** Sine, Cosine, Tangent. Essential for creating repeating patterns like waves or ripples.
        
    - **Power Functions:** Power, Square Root, Logarithm. Useful for changing the falloff curve of a value.
        

**Practical Application:**  
This node is the universal multi-tool for manipulating values in a shader tree. While it has many uses, one of its most powerful functions is using Greater Than to create a sharp, controllable mask from a continuous gradient.

Imagine you are using a Gradient Texture to create a material that transitions from water to an **ice** shelf. You need a sharp, defined line where the ice begins, not a soft, blurry fade.

The problem is that a standard gradient provides a smooth transition from black to white. You need to convert this soft gradient into a hard-edged cutoff. The Math node is the perfect solution.

1. Start with your Gradient Texture (or any other grayscale texture).
    
2. Connect its Factor output to the top Value input of a Math node.
    
3. Set the Operation to Greater Than.
    
4. The bottom Value input now acts as a "threshold" slider. Let's set it to 0.5.
    
5. The node now evaluates every pixel of the gradient: "Is the input value greater than 0.5?" If the answer is yes, it outputs pure white (1.0). If the answer is no, it outputs pure black (0.0).
    
6. The result is that your smooth gradient has been instantly converted into a perfect, hard-edged mask. You can now plug this into the Fac of a Mix Shader that blends between your water and ice materials. By changing the Threshold value, you can interactively move the "ice line" back and forth with perfect sharpness and control.