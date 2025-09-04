**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Deconstructs a 3D vector into its three separate, individual numerical (float) components: X, Y, and Z.

**Key Properties & Settings:**

- **Vector (Input):** The input socket for the vector to be separated. This is commonly connected to a Texture Coordinate or Geometry node.
    
- **X (Output):** A grayscale output providing only the X component of the input vector.
    
- **Y (Output):** A grayscale output providing only the Y component of the input vector.
    
- **Z (Output):** A grayscale output providing only the Z component of the input vector.
    

**Practical Application:**  
This node is fundamental for creating procedural effects that are dependent on an object's position or a specific direction. It allows you to isolate a single axis from a coordinate system to be used as a gradient. Its most common use case is to create a "Z-mask" for effects that should only appear at a certain height on an object, like snow on a mountain.

The problem is how to make a material that is aware of its own height in the world. You need a way to create a mask that is black at the bottom of an object and white at the top. The Separate XYZ node is the ideal solution.

1. Add a Texture Coordinate node and take its Generated or Object output. This provides a coordinate system that is consistent for the object.
    
2. Connect this coordinate vector to the Vector input of a Separate XYZ node.
    
3. The Z output of this node will now be a perfect vertical gradient, black at the bottom of the object's bounding box and fading to white at the top.
    
4. You can connect this Z output to a ColorRamp to precisely control the position and softness of the "snow line."
    
5. Use the output of the ColorRamp as the Fac for a Mix Shader that blends between your "Rock" and "Snow" materials.
    
6. The result is a fully procedural material where snow appears only above a certain height on the object, creating a realistic and art-directable effect that would be difficult to achieve otherwise. This same technique can be used with any axis to create gradients in any direction.