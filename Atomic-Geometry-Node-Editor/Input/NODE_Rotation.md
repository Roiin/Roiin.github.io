- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Outputs a rotation value defined by individual X, Y, and Z Euler angles.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **X, Y, Z (Properties):** Three numeric fields directly on the node to specify the angle of rotation for each corresponding axis.
        
    - **Rotation (Socket - Output):** The combined Euler rotation value.
        
- **Practical Application:** Provides a uniform rotation for multiple objects. For example, if you are creating a row of fence posts by instancing a cylinder onto a mesh line, you can use this node to make them all lean at the same angle. You would set the desired tilt (e.g., 15 degrees on the Y-axis) in the Rotation node and plug its output into the Rotation socket of the Instance on Points node, ensuring every instance is tilted identically.