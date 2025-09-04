- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Import)
    
- **Core Function:** Imports the raw triangular mesh geometry from an external .STL file, making it available as a single mesh within the node tree.
    
- **Key Properties & Settings:**
    
    - **Path (Socket - Input):** A string specifying the file path to the .STL file.
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Mesh (Socket - Output):** The raw mesh geometry imported from the file.
        
- **Practical Application:** This is useful for working with assets from CAD or 3D printing software. For example, an engineer provides a highly detailed mechanical part as a bracket.stl file. The mesh is triangulated and too dense for real-time use. You can use the Import STL node to load this part, then immediately connect it to a Decimate Geometry node to create a simplified, low-polygon version, and then a Set Shade Smooth node to improve its appearance for rendering or animation.