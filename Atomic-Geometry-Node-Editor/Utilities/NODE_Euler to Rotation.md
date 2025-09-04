**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Converts a vector representing Euler angles (in radians) into the standard "Rotation" data type.

**Key Properties & Settings:**

- **Euler (Input):** A vector where the X, Y, and Z components correspond to the angle of rotation around each respective axis.
    
- **Rotation (Output):** The standard rotation data socket output, which can be connected to any rotation input.
    

**Practical Application:**  
This node serves as a clear and explicit way to construct a rotation from individual angle components. While many rotation sockets will implicitly accept a vector as an Euler rotation, using this node makes the node tree's logic easier to read. A common use case is creating a procedural control for a simple hinged object, like a window shutter.

- **The Goal:** To rotate a window shutter around its vertical hinge using a single input slider.
    
- **The Problem:** You have a single float value from a slider (e.g., "Shutter Angle"), but to rotate an object, you need to provide a rotation value. You need to specify which axis this angle should be applied to.
    
- **The Solution:** You construct an Euler rotation vector and then pass it through the Euler to Rotation node for clarity.
    
    1. Start with your shutter geometry (e.g., a thin cube).
        
    2. Use a Combine XYZ node to build the rotation vector. Since the shutter's hinge is vertical, you want to rotate around the Y-axis. Connect your "Shutter Angle" float input into the Y socket of the Combine XYZ node, leaving X and Z as 0.
        
    3. Connect the output vector from Combine XYZ into the Euler input of the Euler to Rotation node.
        
    4. The Rotation output can now be fed into the Rotation socket of a Transform Geometry node that is affecting the shutter.
        

This setup explicitly converts your angle slider into a Y-axis rotation, which is then used to open and close the shutter. It's a robust way to ensure your rotations are being constructed and interpreted correctly.