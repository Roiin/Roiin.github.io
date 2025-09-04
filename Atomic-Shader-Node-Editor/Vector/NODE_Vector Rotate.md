**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Rotates an input vector around a specified pivot point and axis by a given angle.

**Key Properties & Settings:**

- **Vector (Input/Output):** Takes a vector as input (typically texture coordinates) and outputs the rotated vector.
    
- **Type (Property):** The primary control that determines the rotation method. Euler is the most common for artists, providing separate X, Y, and Z rotation inputs. Axis Angle is more advanced, allowing rotation around an arbitrary vector axis.
    
- **Center (Input):** The pivot point for the rotation. By default, it's (0,0,0). For rotating texture coordinates, this should often be set to the center of the texture space (e.g., (0.5, 0.5, 0.5)).
    
- **Angle / Rotation (Inputs):** The inputs that control the amount of rotation. Angle is used for the Axis Angle mode, while the three-component Rotation vector is used for the Euler mode.
    

**Practical Application:**  
This node is essential for creating procedural spiral or vortex effects, which are impossible with standard texture mapping. Imagine you want to create a stylized magical portal or a swirling pool of **molten lava**.

The problem is that a Gradient Texture set to Radial or a Wave Texture set to Rings will only produce straight spokes or perfect circles. They lack the characteristic twist of a vortex. You need a way to rotate the texture coordinates more and more as they get further from the center. The Vector Rotate node is the solution.

1. Start with a Texture Coordinate node (using Generated coordinates). This will be the vector we rotate.
    
2. Add a Vector Rotate node. Set its Center to (0.5, 0.5, 0.5) to ensure the rotation happens around the center of the texture space.
    
3. To create the spiral, the rotation angle must increase with the distance from the center. Calculate this distance by feeding the Texture Coordinate into a Vector Math node set to Length.
    
4. Use a Math node set to Multiply to control the tightness of the spiral. Connect the Length output to the top of the Multiply node and a value (e.g., 10) to the bottom.
    
5. Connect the result of the Multiply node to the Angle input of the Vector Rotate node.
    
6. Finally, connect the Vector output of the Vector Rotate node to a Gradient Texture set to Radial.
    
7. The result is a perfect spiral. The coordinates are twisted by the Vector Rotate node, with the rotation amount determined by the distance from the center, transforming the radial gradient's straight spokes into a swirling vortex pattern.