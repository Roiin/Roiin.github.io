- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a straight line of evenly spaced vertices connected by edges.
    
- **Key Properties & Settings:**
    
    - **Mode (Property):**
        
        - **End Points:** Defines the line by its Start and End locations.
            
        - **Offset:** Defines the line by a Start Location and a repeated Offset vector.
            
    - **Count Mode (Property):** In 'End Points' mode:
        
        - **Count:** Creates a specific total number of vertices.
            
        - **Resolution:** Creates vertices spaced by a specific distance.
            
    - **Count (Socket - Input):** In 'Count' mode, the total number of vertices to create.
        
    - **Start / End Location (Sockets - Input):** The vector positions for the line's endpoints.
        
    - **Mesh (Socket - Output):** The generated line mesh.
        
- **Practical Application:** The Mesh Line is the ideal tool for creating the spine or central nervous system of a procedurally generated animal, like a centipede.
    
    1. **The Spine:** Create a Mesh Line in 'End Points' mode. The Count input now directly controls the number of body segments the centipede will have. A higher count creates a longer centipede.
        
    2. **The Shape:** The straight line is not very organic. You can use a Set Position node and an Offset driven by a Noise Texture (with the Index plugged into its vector input) to give the spine a natural, slithering curve.
        
    3. **The Body:** Now that you have a curved line of points, you can use Instance on Points to place the body segments. For each point on the line, instance a scaled cube for the main body and two cylinders for the legs.
        
    4. **The Orientation:** To make the segments follow the curve, you can calculate the tangent direction (the vector from the current point to the next point) and use an Align Euler to Vector node to orient the instances correctly.
        
    5. The Mesh Line node served as the fundamental, controllable "skeleton" for the entire creature. Changing the Count parameter on this single node allows you to instantly change the length and number of segments of the final, complex centipede model.