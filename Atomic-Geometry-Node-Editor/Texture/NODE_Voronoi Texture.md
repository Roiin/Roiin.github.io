- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates Worley noise, which is characterized by a pattern of cells. The node can output various data about these cells, such as the distance to the nearest cell's center, the distance to its edge, or a random color for each cell.
    
- **Key Properties & Settings:**
    
    - **Dimensions (Property):** Sets the evaluation space (1D, 2D, 3D, 4D).
        
    - **Feature (Property):** The core control that determines what data the node calculates:
        
        - **F1:** Finds the closest cell point.
            
        - **F2:** Finds the second-closest cell point.
            
        - **Smooth F1:** A smoothed version of F1, useful for blending.
            
        - **Distance to Edge:** Calculates the distance to the nearest boundary between cells. This is perfect for creating cracked or cellular patterns.
            
        - **N-Sphere Radius:** Calculates the radius of the largest sphere that can fit inside each cell.
            
    - **Distance Metric (Property):** The mathematical formula used to calculate distance ('Euclidean', 'Manhattan', etc.), which changes the shape of the cells from rounded to square or diamond-like.
        
    - **Vector (Socket - Input):** The coordinate space to evaluate the noise in.
        
    - **Scale (Socket - Input):** Controls the overall size and density of the cells.
        
    - **Randomness (Socket - Input):** A float from 0 to 1. At 0, the cells form a perfect, regular grid. At 1, they are completely randomly distributed.
        
    - **Distance (Socket - Output):** Outputs the calculated distance value (e.g., to the cell center or edge).
        
    - **Color (Socket - Output):** Outputs a unique, random color for each individual cell.
        
    - **Position (Socket - Output):** Outputs the position of the center of the cell that each sample point belongs to.
        
- **Practical Application:** The Distance to Edge feature is ideal for creating procedural cracked earth or the scale patterns on a reptile.
    
    1. **The Goal:** To create a cracked, dry mud pattern on a flat plane, with the cracks being physically recessed into the surface.
        
    2. Start with a highly subdivided Grid.
        
    3. Use the Voronoi Texture node. Set the Feature to 'Distance to Edge'.
        
    4. The Distance output is now a gradient that is black (0.0) on the cell edges (the "cracks") and fades to white towards the center of each cell.
        
    5. Use a Color Ramp node to sharpen this gradient, creating a crisp, vein-like pattern for the cracks.
        
    6. Use a Set Position node on your grid.
        
    7. For the Offset, you want to push the "not crack" parts up. Multiply your final crack pattern by the mesh Normal and a negative value (to push the cracks down, or a positive value to push the plates up).
        
    8. **The Result:** A flat plane is displaced into a realistic 3D surface of cracked mud. The Voronoi Texture procedurally defined the complex network of cracks. This same technique can be used with a low Randomness to create the more regular scale or scute patterns on an animal like a tortoise or a crocodile.