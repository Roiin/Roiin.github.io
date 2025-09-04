**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Performs a vast array of mathematical operations on floating-point values, from basic arithmetic to complex trigonometric functions.

**Key Properties & Settings:**

- **Operation (Dropdown):** Selects the function to be performed. The list is extensive, but key operations include:
    
    - **Functions:** Add, Subtract, Multiply, Divide, Power, Square Root.
        
    - **Rounding:** Round, Floor, Ceil, Truncated Modulo.
        
    - **Trigonometric:** Sine, Cosine, Tangent, Arctan2. These are crucial for creating waves, spirals, and rotations.
        
    - **Comparison:** Minimum, Maximum, Less Than, Greater Than.
        
- **Inputs:** The input sockets are dynamic and change based on the selected operation. Most have one or two Value inputs.
    
- **Clamp (Checkbox):** When enabled, this limits the output to the standard 0.0 to 1.0 range.
    
- **Value (Output):** The single float result of the mathematical operation.
    

**Practical Application:**  
The trigonometric functions in the Math node are indispensable for creating organic, oscillating motion. A perfect example is creating a procedural animation of a line of particles moving in a smooth, continuous wave, like the locomotion of a snake or the undulation of a fish's fin.

- **The Goal:** To displace a straight line of points vertically in a sine wave pattern.
    
- **The Problem:** You cannot create a wave shape by simply moving the points; each point's vertical offset must be calculated individually based on its position along the line.
    
- **The Solution:** The Sine function maps a linear input to a smooth, repeating -1 to 1 curve.
    
    1. Start with a Line mesh primitive to create your initial row of points.
        
    2. Use a Set Position node to modify the points' location.
        
    3. Isolate the X coordinate of each point's Position using a Separate XYZ node. This will be the input that drives the wave.
        
    4. Feed the X position into a Math node set to Sine. The output is now a smooth wave pattern. To animate this wave, you can use another Math (Add) node to add the scene's current Time (or frame number) to the X position before it enters the Sine node.
        
    5. To control the wave's height (amplitude), take the output of the Sine node and use a Math (Multiply) node to scale it.
        
    6. Use a Combine XYZ node to construct the final offset vector. Leave X and Y at 0, and plug the result of your multiply node into the Z input.
        
    7. Connect this final vector to the Offset input of the Set Position node.
        

The result is a perfectly smooth, animatable wave running through your line of particles, a foundational effect for creating everything from swimming animals to waving flags.