**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Constructs a single 3D vector from three separate, individual numerical inputs for the X, Y, and Z components.

**Key Properties & Settings:**

- **Vector (Output):** The final, combined vector.
    
- **X (Input):** A socket for a single numerical value (float) that will become the X component of the output vector.
    
- -**Y (Input):** A socket for a single numerical value that will become the Y component.
    
- **Z (Input):** A socket for a single numerical value that will become the Z component.
    

**Practical Application:**  
This node is essential for procedurally generating or modifying texture coordinates and other vectors. It is the counterpart to the Separate XYZ node and allows you to manipulate the axes of a vector independently before reassembling them.

A classic and powerful use case is creating procedural **wood grain**. The problem is that a standard Noise Texture creates round, blobby patterns, whereas wood grain is made of long, stretched fibers. You need to stretch the texture coordinates along one axis. The Combine XYZ node (along with its Separate XYZ partner) provides a clean way to do this.

1. Start with a Texture Coordinate node.
    
2. Add a Separate XYZ node and connect the Generated or Object coordinates to its Vector input. This breaks the coordinate vector into three separate, editable channels: X, Y, and Z.
    
3. Add a Math node set to Multiply. Connect the Y output of the Separate XYZ node into the top slot of the Math node. In the bottom slot, enter a large value like 0.1. This will "squash" the coordinates along the Y-axis.
    
4. Now, add a Combine XYZ node. Connect the original X output directly to the X input. Connect the output of your Math node to the Y input. Connect the original Z output directly to the Z input.
    
5. You have now reassembled the vector, but with a modified Y component. Connect the Vector output of the Combine XYZ node to the Vector input of a Noise Texture.
    
6. The result is that the noise pattern is now stretched into long, fibrous streaks, perfectly mimicking the look of wood grain. This method of separating, modifying, and recombining a vector is a fundamental technique in procedural texturing.