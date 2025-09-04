**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Provides a user-defined direction vector and can also calculate the dot product between this vector and another input normal.

**Key Properties & Settings:**

- **Normal (Output):** The primary output, providing a normalized vector based on the direction set in the node's properties.
    
- **Dot (Output):** A grayscale output representing the dot product (the angular relationship) between the node's direction and an incoming Normal vector. It is white (1.0) when the vectors are parallel, gray (0.0) when they are perpendicular, and black (-1.0) when they are opposed.
    
- **Normal Direction (Property):** The main interface. A spherical widget that allows you to visually set the direction vector by clicking and dragging. This vector is then provided at the Normal output.
    
- **Normal (Input):** A socket to provide an incoming normal, typically from a Geometry or Texture Coordinate node, which is then compared against the node's direction to calculate the Dot product.
    

**Practical Application:**  
The Dot product output is an exceptionally powerful tool for creating direction-based material effects, such as adding a layer of snow or dust that settles only on upward-facing surfaces.

The problem is how to procedurally create a mask that isolates only the tops of objects, regardless of their shape or orientation. You need a way to ask the material, "Is this part of your surface pointing up?" The Normal node is the solution.

1. In your material, add a Normal node. By default, its direction vector points straight up along the Z-axis (0, 0, 1), which is exactly what we need for a "snow" direction.
    
2. Add a Geometry node and connect its Normal output to the Normal input of the Normal node. This feeds the surface normal of every point on your object into the node for comparison.
    
3. The Dot output will now be a grayscale mask. Surfaces that are pointing straight up will be white, surfaces that are vertical (like the sides of a wall) will be mid-gray, and surfaces pointing down will be black.
    
4. To create a sharp mask, connect this Dot output to a ColorRamp node and crush the values so that only the nearly-white values remain white, and everything else becomes black.
    
5. You can now use this mask as the Fac for a Mix Shader that blends between your base material (e.g., **rust**y metal) and a "Snow" shader. The snow will now appear only on the upward-facing surfaces, creating a highly realistic and fully procedural snow-fall effect.