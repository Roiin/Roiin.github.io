- **Editor:** Compositor Node Editor
- **Node Group:** Vector
    
- **Core Function:** Performs a selected mathematical operation on one or two input vectors, outputting either a new vector or a single scalar value.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket - Input):** The first input vector, often used as the primary subject of the operation.
        
    - **Vector (Socket - Input):** The second input vector, used for two-vector operations like Add or Distance.
        
    - **Operation (Property):** The mathematical function to perform. Key modes for compositing include Add, Subtract, Distance, Length, Dot Product, and Normalize. The node's inputs and outputs change based on this selection.
        
    - **Vector (Socket - Output):** The resulting vector from the operation (e.g., for Add, Normalize).
        
    - **Value (Socket - Output):** The resulting single float value from the operation (e.g., for Distance, Length).
        
- **Practical Application:** This node is essential for creating 3D-aware masks and effects inside the compositor. A powerful technique is to generate a procedural "limelight" or spotlight effect that exists in the 3D space of the render, using the Distance operation.
    
    1. Start with a **Render Layers** node (or an **Image** node loading a multi-layer EXR) that has the **Position** pass enabled. The Position pass contains the world-space XYZ coordinates for every pixel in the image.
        
    2. Add a **Vector Math** node and set its Operation to Distance.
        
    3. Connect the Position pass output into the first Vector input of the **Vector Math** node.
        
    4. To define the center of your spotlight, add a **Combine XYZ** node. The three values of this node represent the XYZ coordinate in your 3D scene where the light will be centered. Connect its Vector output to the second Vector input of the **Vector Math** node.
        
    5. The Value output of the **Vector Math** node now produces a grayscale gradient. It is black (a distance of 0) at the exact XYZ coordinate you defined and gets progressively whiter as the pixels get further away from that point in 3D space.
        
    6. To control the falloff, connect this Value output to a **Color Ramp** node. You can invert the ramp and move the stops to create a soft, circular mask that is perfectly mapped to the surfaces in your scene.
        
    7. Use the output of the **Color Ramp** as the Factor for an **Exposure** or **Color Balance** node to brighten your main beauty pass. The result is a spotlight effect that realistically wraps around corners and sticks to objects as if it were part of the original 3D scene.