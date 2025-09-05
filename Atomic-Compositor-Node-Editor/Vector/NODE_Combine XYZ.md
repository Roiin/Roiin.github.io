- **Editor:** Compositor Node Editor
- **Node Group:** Vector
    
- **Core Function:** Constructs a single 3D vector output from three separate scalar (floating-point) input values.
    
- **Key Properties & Settings:**
    
    - X ([Socket]): The floating-point value to be used for the X component of the vector.
        
    - Y ([Socket]): The floating-point value to be used for the Y component of the vector.
        
    - Z ([Socket]): The floating-point value to be used for the Z component of the vector.
        
    - Vector ([Socket]): The resulting 3D vector (X, Y, Z).
        
- **Practical Application:**
    
    - **Molecular (Precise Color Assembly):** While a color input socket seems direct, this node offers procedural control. You can create a "molecule" by feeding the output of three different **Math** nodes or **Noise Textures** into the X, Y, and Z inputs. In the Compositor or Shader editor, this translates to the R, G, and B channels, allowing you to build a final color where each channel is driven by a completely independent procedural logic.
        
    - **Molecular (Directional Offset):** This is a fundamental "atom" for any procedural positioning. To move an object or displace a texture only along a single axis, feed a value into just one input (e.g., the Z input) while leaving the others at 0. The output is a clean directional vector. This simple "molecule" is the basis for countless effects in Geometry Nodes, such as instancing objects in a straight line or extruding faces purely upwards.
        
    - **Organic (Complex Procedural Animation):** In Geometry Nodes, this node is essential for creating sophisticated "organisms" of motion. You can drive the X input with a **Math** node set to Sine, the Y input with a Cosine, and the Z input with the output of a **Noise Texture** whose W value is animated over time. The **Combine XYZ** node takes these three independent streams of data and assembles them into a single Position vector, creating a swirling, bobbing, and organic animation path for your instances without using a single keyframe.
        
    - **Organic (Procedural Vector Generation):** This node is key to creating custom vectors for more advanced nodes like the **Vector Rotate** or **Normal Map** nodes. For example, to create a procedural "wind" force in a simulation, you can use **Combine XYZ** to build the wind's direction vector. You could animate the X and Y inputs with slow-moving **Noise Textures** to simulate gusting and shifting wind directions, creating a far more believable and dynamic "organism" than a simple static vector.