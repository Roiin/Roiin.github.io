- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** For each top-level instance, this node calculates its axis-aligned bounding box and outputs the local-space coordinates of its minimum and maximum corners. This is the primary method for getting the "size" or spatial dimensions of an instance.
    
- **Key Properties & Settings:**
    
    - **Instances (Socket - Input):** The geometry containing the instances to be measured.
        
    - **Use Radius (Socket - Input):** A Boolean. For curves and point clouds, if True, it includes the radius attribute in the size calculation, providing a more accurate bounding box for thickened curves.
        
    - **Min (Socket - Output):** A vector field representing the local-space position of the bounding box corner with the lowest X, Y, and Z values for each instance.
        
    - **Max (Socket - Output):** A vector field representing the local-space position of the bounding box corner with the highest X, Y, and Z values for each instance.
        
- **Practical Application:** This node is perfect for creating geometry that needs to adapt to the size of an instance, like procedurally generating packaging for a product.
    
    1. Imagine you have a Collection Info node that brings in one of many different animal toys (a tall giraffe, a wide crocodile, a compact bear). You instance one of these toys.
        
    2. **The Goal:** You want to create a simple cardboard box that perfectly fits whichever toy is chosen.
        
    3. Use the Instance Bounds node on the toy instance. The Min and Max outputs now give you the dimensions of the toy.
        
    4. You can get the total size of the toy by subtracting the Min vector from the Max vector (Size = Max - Min).
        
    5. Create a Cube primitive for your box. Feed this calculated Size vector directly into the Size input of the Cube node.
        
    6. To position the box correctly, you can find the center of the toy's bounding box by adding Min and Max and dividing by two (Center = (Min + Max) / 2). Use this to set the position of the cube.
        
    7. The result is a procedural system where if you switch the instanced toy from the tall giraffe to the wide crocodile, the surrounding box will instantly and automatically resize itself to be a perfect fit.