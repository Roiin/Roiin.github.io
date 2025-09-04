- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a cube or cuboid (rectangular prism) mesh.
    
- **Key Properties & Settings:**
    
    - **Size (Socket - Input):** A vector that controls the dimensions of the cube along the X, Y, and Z axes.
        
    - **Vertices X, Y, Z (Sockets - Input):** Integers that control the number of subdivisions along each axis. A value of 2 (the default) creates a simple cube with no subdivisions.
        
    - **Mesh (Socket - Output):** The generated cube mesh.
        
    - **UV Map (Socket - Output):** A default, unwrapped UV map for the cube, ready to be stored as an attribute for texturing.
        
- **Practical Application:** The Cube node is the versatile starting point for an enormous range of procedural models, especially hard-surface objects like a crate for an animal transport.
    
    1. **The Goal:** To create a wooden shipping crate.
        
    2. **The Base:** Start with a Cube node. You can set the Size to create the main rectangular shape.
        
    3. **The Planks:** To create the appearance of wooden planks, increase the Vertices count on one or two axes (e.g., Vertices X = 8). This adds edge loops.
        
    4. **The Gaps:** You can then select every other face along that axis (using the Index and a Modulo math operation) and use Scale Elements to slightly shrink them. This creates the illusion of separate planks with gaps between them.
        
    5. **The Frame:** To create a reinforced frame, you can Separate Geometry using the corner edges of the original cube, convert them to curves with Mesh to Curve, and then give them thickness with Curve to Mesh.
        
    6. **The Result:** By starting with a simple Cube and applying a series of procedural operations, you can build a detailed and non-destructive crate model. The Cube serves as the fundamental block of wood from which the entire object is procedurally carved and assembled.