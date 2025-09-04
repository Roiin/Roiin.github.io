**Editor:** Shader Editor 
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Retrieves specific data attributes—such as vertex colors or custom properties—from an object or mesh, making them available to use within the shader tree.

**Key Properties & Settings:**

- **Name:** A text field where you enter the specific name of the attribute you wish to access (e.g., the name of a vertex color layer, like the default "Col").
    
- **Attribute Type:** Specifies the context from which to pull the data. The most common are Geometry (for per-vertex data like vertex colors) and Object (for per-object data like Custom Properties).
    
- **Color (Output):** Outputs the retrieved attribute interpreted as color data. Ideal for using vertex color layers.
    
- **Factor (Output):** Outputs the retrieved attribute as a single grayscale value.
    
- **Vector (Output):** Outputs the retrieved attribute as 3D vector data.
    

**Practical Application:**  
This node is essential for giving artists direct, paintable control over a material. Imagine creating a **stylized skin** material for a character and needing to add a subtle blush to the cheeks.

The problem is that procedural noise can't place the blush in an exact, artist-defined location. You need to "paint" the effect on. The Attribute node is the solution for reading that painted data.

1. In Blender's Vertex Paint mode, you can directly paint color onto the model's cheeks. This information is stored in a vertex color attribute, typically named "Col".
    
2. In the Shader Editor, add an Attribute node and type "Col" into its Name field.
    
3. The Color output of the node will now contain the blush color you painted, isolated on a black background.
    
4. You can use this output as a mask. For example, connect it to the Fac of a Mix Color node that blends your base skin tone with a reddish blush color. This allows you to precisely control the location and intensity of the blush effect by simply painting it onto the model, bridging the gap between artistic input and procedural shading.