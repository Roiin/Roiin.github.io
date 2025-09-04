**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Read)

**Core Function:** Provides specific information about the first point (the "root") of each hair curve.

**Key Properties & Settings:**

- **Root Selection (Output):** A boolean field that is True only for the first control point of every curve and False for all other points.
    
- **Root Position (Output):** The 3D position vector of the root point of each curve.
    
- **Root Direction (Output):** The tangent vector of the very first segment of the curve, indicating the direction the hair is growing out from the surface.
    
- **Root Index (Output):** The index of the root point within the overall list of all points in the curve geometry component.
    

**Practical Application:**  
This node is essential for creating effects that are anchored to the base of the hair, such as instancing objects at the root. Imagine you are creating a stylized tree where you want to add a visible, thickened root ball at the base of every single branch.

- **The Goal:** To instance a small sphere at the exact location of the first point of every curve that defines a tree branch.
    
- **The Problem:** The Instance on Points node needs a selection to know which points to instance on. If you connect the entire tree curve geometry, it will instance spheres on every point along the branches, not just the roots.
    
- **The Solution:** The Curve Root node provides the perfect selection mask.
    
    1. Start with your procedurally generated tree geometry, which is made of curves.
        
    2. Add an Instance on Points node. Connect the tree curves to the Points input.
        
    3. Add a Curve Root node.
        
    4. Connect its Root Selection output directly into the Selection input of the Instance on Points node.
        
    5. Use a UV Sphere or similar primitive as the Instance geometry.
        

The Instance on Points node will now only create spheres at the points where the Root Selection is True. This results in a single sphere being placed perfectly at the base of the trunk and at the start of every subsequent branch, creating the desired root ball effect.