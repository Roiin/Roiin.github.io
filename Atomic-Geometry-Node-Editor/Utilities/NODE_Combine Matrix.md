**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Constructs a full 4x4 transformation matrix from sixteen individual float values.

**Key Properties & Settings:**

- **Column Inputs (1-4):** Four panels, each containing four float inputs. These represent the sixteen components of the matrix that define an object's location, rotation, and scale in 3D space.
    
- **Matrix (Output):** The final 4x4 transformation matrix.
    

**Practical Application:**  
This node provides the lowest-level control over transformations, allowing you to create effects like shearing, which are not directly available in standard transform nodes. Imagine you want to create a procedural stack of paper or a deck of cards that has been pushed from the side, causing it to slant.

- **The Goal:** To apply a non-uniform shear transformation to a cube, making it look slanted.
    
- **The Problem:** The standard Transform Geometry node has inputs for Location, Rotation, and Scale, but it does not have a "Shear" input. You cannot create this slanting effect using the basic transform controls.
    
- **The Solution:** The Combine Matrix node allows you to build a custom transformation matrix from scratch that includes shearing.
    
    1. Start with a Cube primitive representing your stack of paper.
        
    2. Add a Transform Geometry node. This node's Transformation input can accept a matrix.
        
    3. Use a Combine Matrix node to construct the shear matrix. To start, you would create an "identity matrix" which does nothing: set the diagonal values (the first input of the first column, second of the second, etc.) to 1.0 and all other fourteen values to 0.0.
        
    4. To introduce a shear that slants the object along the X-axis as it goes up the Z-axis, you modify a single value. In the third column (which maps the Z-axis), change the first value (which outputs to the X-axis) from 0.0 to 0.5.
        
    5. Connect the Matrix output from the Combine Matrix node into the Transformation socket of the Transform Geometry node.
        

The result is that the cube is now slanted. The top of the cube is pushed along the X-axis, while the bottom remains in place. This gives you direct, mathematical control to create advanced transformations that are impossible with simpler nodes.