- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates a classic 2D or 3D checkerboard pattern.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket - Input):** The coordinate space to evaluate the texture in. By default, uses the object's Position, creating a 3D checker pattern. Plugging in a 2D UV map will create a 2D pattern on the surface.
        
    - **Color 1 / Color 2 (Sockets - Input):** The two alternating colors of the checker pattern.
        
    - **Scale (Socket - Input):** A float that controls the size of the checker squares. Higher values result in smaller squares.
        
    - **Color (Socket - Output):** The final colored texture output.
        
    - **Factor (Socket - Output):** A black and white mask where one set of squares is white (1.0) and the other is black (0.0).
        
- **Practical Application:** The Factor output is perfect for creating selections to model physical checkerboards or tiled floors.
    
    1. **The Goal:** To create a 3D checkerboard with raised black squares and lowered white squares.
        
    2. Start with a Grid primitive with a moderate number of subdivisions.
        
    3. Use the Checker Texture node. Feed the grid's Position (or its UV map) into the Vector input. Adjust the Scale so that the checker pattern aligns nicely with your grid.
        
    4. The Factor output is now a Boolean-like selection for one set of squares.
        
    5. Use a Separate Geometry node with this Factor as the Selection. You now have two separate meshes: one for the "black" squares (Selection output) and one for the "white" squares (Inverted output).
        
    6. Use a Transform Geometry node on the "black" squares mesh and translate it slightly upwards on the Z-axis.
        
    7. Use a Join Geometry node to combine the raised black squares with the original white squares. You can also assign different materials to each set before joining.
        
    8. **The Result:** A physical, 3D checkerboard where the two sets of squares are at different heights, all generated procedurally from a single flat grid.