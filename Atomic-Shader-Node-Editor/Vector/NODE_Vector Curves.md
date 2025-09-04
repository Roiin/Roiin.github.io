**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Provides a curve-based interface to remap the individual X, Y, and Z components of an input vector, allowing for non-linear transformations.

**Key Properties & Settings:**

- **Vector (Input/Output):** Takes a vector as input and outputs the remapped vector.
    
- **Curve (Property):** The primary interface. It is a graph where the horizontal axis represents the input value for a given component (from 0 to 1) and the vertical axis represents the remapped output value.
    
- **Channel (Property):** A set of buttons (X, Y, Z) that allows you to switch between editing the curve for each of the vector's components independently.
    
- **Fac (Input):** A factor to control the overall strength of the node's effect, blending between the original and the remapped vector.
    

**Practical Application:**  
This node is excellent for creating advanced, non-linear distortion effects on texture coordinates. Imagine you want to create a stylized "warp" or "fisheye lens" effect directly in your material, where a texture appears normal in the center but becomes increasingly stretched and distorted towards the edges.

The problem is that a standard Mapping node can only perform linear transformations (uniform scaling, rotation, and translation). It cannot create a distortion that changes its intensity based on position. The Vector Curves node is the solution.

1. Start with a Texture Coordinate node, using its Generated output.
    
2. Add a Vector Curves node and pass the coordinates through it.
    
3. Switch to editing the X channel. Change the default linear line into a curve that is flat in the middle and becomes very steep at the ends. This means that X-coordinates near the center (0.5) will be remapped with little change, while coordinates near the edges (0 and 1) will be pushed aggressively outwards.
    
4. Do the same for the Y channel.
    
5. Connect the output of the Vector Curves node to the Vector input of any procedural texture, like a Checker Texture.
    
6. The result will be a dramatic distortion. The checker pattern will appear normal in the center of the object, but towards the edges, the squares will become increasingly stretched and warped according to the shape of your curves, creating a complex, non-linear effect that would be impossible with a simple Mapping node.