**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Deforms the mesh at render time using a color texture (a vector displacement map) that defines not just the height but the full X, Y, and Z direction of the displacement for each point, allowing for complex overhangs and undercuts.

**Key Properties & Settings:**

- **Displacement (Output):** The node's only output, providing the directional offset. It must be connected only to the Displacement socket of the Material Output node.
    
- **Vector (Input):** The input for a color Image Texture containing the vector displacement map. The RGB values of the image are interpreted as XYZ displacement directions.
    
- **Scale (Input):** A simple multiplier that controls the overall strength and distance of the displacement effect.
    
- **Space (Property):** The coordinate system in which the map was baked. Tangent space is essential for deforming objects like characters, while Object space is for static models.
    
- **CRITICAL WORKFLOW:** The Image Texture node containing the vector displacement map must have its Color Space set to Non-Color. You must also go to the Material Properties, expand Settings, and change the Displacement option to Displacement Only or Displacement and Bump.
    

**Practical Application:**  
This node is essential for recreating extremely complex sculpted details that go beyond simple height changes, such as fins, horns, or deep grooves. Imagine you have sculpted a highly detailed creature with large, curling horns and overlapping scales, but you need to render it on a much simpler, animation-friendly base mesh.

The problem is that a standard Displacement node can only push the surface in or out along its normal; it cannot create overhangs like the curve of a horn or the lip of a scale. The Vector Displacement node is the solution.

1. First, you would bake a "Vector Displacement Map" from your high-poly sculpt onto the UVs of your low-poly base mesh. This creates an RGB image that stores the full directional information.
    
2. On the low-poly mesh, add a Subdivision Surface modifier to provide enough geometry for the displacement.
    
3. In the shader, add an Image Texture node, load your vector displacement map, and critically, set its Color Space to Non-Color.
    
4. Add a Vector Displacement node. Connect the Image Texture's Color output to the Vector input.
    
5. Connect the Vector Displacement node's output to the Displacement socket on the Material Output node.
    
6. Finally, set the material's Displacement method to Displacement Only.
    
7. The result is that the simple base mesh will be dramatically re-shaped at render time into the full, complex form of the original sculpt. The node reads the directional data from the texture and is able to push vertices sideways and create the complex overhangs of the horns and scales, faithfully recreating the high-poly detail in a way that is impossible with any other method.