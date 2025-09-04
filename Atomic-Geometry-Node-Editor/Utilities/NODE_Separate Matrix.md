**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Deconstructs a 4x4 transformation matrix into its sixteen individual float components.

**Key Properties & Settings:**

- **Matrix (Input):** The 4x4 matrix to be split.
    
- **Column Outputs (1-4):** Four panels, each containing four float outputs. These represent the sixteen values of the matrix, column by column.
    

**Practical Application:**  
This node is useful for extracting specific data, like the world-space position, from a complex transformation matrix. Imagine you have a procedurally animated spider leg, built from several segments chained together with Multiply Matrices. You need to find the exact world position of the very tip of the final leg segment, perhaps to create a particle effect like a venom drip.

- **The Goal:** To get the precise X, Y, Z location of the tip of a procedurally animated spider leg.
    
- **The Problem:** The final transformation of the leg tip is contained within a complex 4x4 matrix. This matrix holds rotation and scale information in addition to location. You cannot use the matrix directly to set an object's position; you need to isolate only the translation vector.
    
- **The Solution:** The Separate Matrix node can deconstruct the matrix to reveal this information.
    
    1. Take the final, combined transformation matrix that defines the leg tip's pose.
        
    2. Connect this matrix to the Matrix input of the Separate Matrix node.
        
    3. A standard transformation matrix stores its location (translation) data in the first three rows of its fourth column.
        
    4. Take the first three float outputs from the "Column 4" output panel. These are the X, Y, and Z coordinates of the leg tip.
        
    5. Use a Combine XYZ node to reassemble these three float values into a single position vector.
        

This resulting vector is the exact world-space location of the spider's leg tip. You can now use this vector to precisely place a venom drip particle or any other geometric detail.