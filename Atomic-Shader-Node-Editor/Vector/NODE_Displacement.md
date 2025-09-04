**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Physically deforms the mesh at render time based on a height texture, creating true geometric detail and altering the object's silhouette.

**Key Properties & Settings:**

- **Displacement (Output):** The node's only output. It provides a vector offset and must be connected only to the Displacement socket of the Material Output node.
    
- **Height (Input):** The input for a grayscale texture (height map). White values are displaced outwards, black values are displaced inwards.
    
- **Midlevel (Input):** Sets the "zero point" for the displacement. At the default of 0.5, any 50% gray in the height texture will cause no displacement. Values above 0.5 push outwards, and values below push inwards.
    
- **Scale (Input):** A simple multiplier that controls the overall strength and distance of the displacement effect.
    
- **CRITICAL SETTING:** For this node to work as true displacement, you must go to the Material Properties tab, expand the Settings panel, and change the Displacement option from "Bump Only" to "Displacement Only" or "Displacement and Bump".
    

**Practical Application:**  
This node is essential when you need to create surface detail that is significant enough to affect the object's geometry and silhouette, an effect that simple bump mapping cannot achieve. It is perfect for creating a block of rough, natural **ice**.

The problem is that a standard ice material on a simple cube will look like a perfectly smooth, polished piece of glass. Bump mapping can add a bit of surface texture, but the cube's silhouette will remain a perfectly straight line, which looks artificial. You need the surface to be genuinely uneven and chunky. The Displacement node is the solution.

1. Start with a cube and add a Subdivision Surface modifier to it, set to Simple with a high number of subdivisions (e.g., 6). True displacement requires dense geometry to work with.
    
2. In the shader, create your base ice material using a Principled BSDF.
    
3. Add a Noise Texture with a low Detail value to create a simple, blobby pattern.
    
4. Add a Displacement node. Connect the Noise Texture's Factor output to the Height input.
    
5. Connect the Displacement node's Displacement output to the Displacement socket on the final Material Output node.
    
6. Finally, perform the critical step: in the Material Properties, change the Displacement method to Displacement and Bump.
    
7. The result is a dramatic transformation. The flat faces of the cube are now physically pushed and pulled by the noise texture, creating a truly rough, uneven, and organic surface. The silhouette is no longer a straight line but is now jagged and irregular, turning a simple geometric primitive into a believable block of natural ice.