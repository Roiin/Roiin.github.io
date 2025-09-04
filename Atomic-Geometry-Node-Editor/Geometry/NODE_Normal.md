- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Outputs the direction that each element of a geometry is facing, known as its normal vector. The meaning of this 'normal' vector changes depending on the context (e.g., for a face, it's the perpendicular direction; for a vertex, it's the averaged direction of its surrounding faces). The output is always a normalized unit vector.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Normal (Socket - Output):** A vector field representing the normal of each geometry element. This output respects custom normals if they exist on the mesh.
        
    - **True Normal (Socket - Output):** A vector field representing the geometrically calculated normal, ignoring any custom normal data that may be present on the mesh.
        
- **Practical Application:** This node is fundamental for aligning instances to a surface. For example, if you scatter points on a sphere using the Distribute Points on Faces node, that node automatically provides the Normal for each point. You can then feed this Normal vector into an Align Euler to Vector node. The output of that node can be plugged directly into the Rotation socket of an Instance on Points node. This will ensure that every instanced object (like a cone or a tree) is perfectly oriented to point directly away from the sphere's surface, following its curvature.