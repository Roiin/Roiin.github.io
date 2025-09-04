- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Write)
    
- **Core Function:** For NURBS and Bézier splines, this node procedurally sets their resolution, which controls how many points are used to approximate the curve between control points. Higher values result in a smoother, more detailed curve.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The curve geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. The resolution will only be changed on splines where this is True.
        
    - **Resolution (Socket - Input):** An integer field providing the new resolution value.
        
    - **Curve (Socket - Output):** The curve, now with its updated resolution.
        
- **Practical Application:** This node is perfect for creating a Level of Detail (LOD) system for complex procedural assets like a tree.
    
    1. Imagine your tree is generated from a collection of curved branches. When the tree is close to the camera, you want the branches to be smooth and high-quality. When it's far away, you want them to be simpler to save performance.
        
    2. Use the Active Camera and Object Info nodes to get the camera's position. Calculate the Distance from the camera to the tree.
        
    3. Use a Map Range node. Map the Distance (e.g., from 10m to 100m) to a new range of integer Resolution values (e.g., from 12 down to 2). Use a Float to Integer node to ensure the output is a whole number.
        
    4. Feed this calculated, distance-dependent integer into the Resolution input of the Set Spline Resolution node, which is applied to your branch curves before they are converted to a mesh.
        
    5. The result is a dynamic LOD system. As you move the camera away from the tree, the resolution of its branches automatically decreases, simplifying the final mesh and improving performance. As you move closer, the resolution increases, restoring the visual quality.