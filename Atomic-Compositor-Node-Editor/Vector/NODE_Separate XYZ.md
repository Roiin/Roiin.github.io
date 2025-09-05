- **Editor:** Compositor Node Editor
- **Node Group:** Vector
    
- **Core Function:** Deconstructs a single vector input into its three separate scalar (floating-point) components.
    
- **Key Properties & Settings:**
    
    - Vector ([Socket]): The input vector to be split into its constituent parts.
        
    - X ([Socket]): The output value corresponding to the X component of the input vector.
        
    - Y ([Socket]): The output value corresponding to the Y component of the input vector.
        
    - Z ([Socket]): The output value corresponding to the Z component of the input vector.
        
- **Practical Application:**
    
    - **Molecular (Up-Facing Mask):** A classic "molecule" for procedural texturing is to create a mask for surfaces that point upwards. Feed the Normal output from a **Texture Coordinate** or **Geometry** node into the **Separate XYZ** node. The Z output will now be a grayscale map where flat, upward-facing surfaces are white (value of 1) and vertical faces are black (value of 0). This output can be used directly or refined with a **Color Ramp** to create effects like snow, dust, or moss on the top of an object.
        
    - **Molecular (Positional Driver):** This node is excellent for using one attribute to drive another. You can take the Position vector of an object, **Separate** it, and use the individual X, Y, or Z outputs to control completely unrelated properties. For example, use the X position to drive the Scale of a procedural texture, while the Z position drives its Emission Strength. This creates an effect that changes dynamically as the object moves through the scene.
        
    - **Organic (World-Space Gradient):** A powerful "organism" in procedural shading involves using an object's world position to control shaders. By taking the Position attribute and separating it with **Separate XYZ**, you can isolate the Z component (world height). This value can then be fed into a complex chain of **Map Range** and **Color Ramp** nodes to create a gradient that is consistent across all objects in your scene. This is a professional workflow for adding effects like a rising water level, ground fog that hugs the terrain, or distinct material changes based on altitude (e.g., rock to grass to snow on a mountain).
        
    - **Organic (Conditional Geometry Generation):** In Geometry Nodes, **Separate XYZ** is a cornerstone of logical control. Imagine an "organism" that procedurally generates a city block. You can distribute points on a grid, **Separate** their Position vector, and use the X and Y outputs with **Math** nodes (like Modulo) to decide where to instance buildings versus where to leave empty space for roads. Simultaneously, you can use the Z output from the position of points on those buildings to change their details based on height—creating a ground-floor lobby, repeating office windows, and a stylized rooftop, all driven by separating a single position vector.