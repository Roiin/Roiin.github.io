- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Import)
    
- **Core Function:** Imports the mesh geometry from a .PLY file, preserving vertex attributes like color and normals, and outputs it as a single mesh.
    
- **Key Properties & Settings:**
    
    - **Path (Socket - Input):** A string specifying the file path to the .PLY file.
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Mesh (Socket - Output):** The mesh geometry imported from the file.
        
- **Practical Application:** This is highly useful for integrating 3D scanned assets. For example, if you have a photogrammetry_rock.ply file from a 3D scan, you can import it using this node. The scan might have an unwanted flat base. Because the output is a single mesh, you can immediately connect it to nodes like Delete Geometry to procedurally trim off the flat base, and then use other nodes to add details or scatter moss onto its surfaces, seamlessly integrating the scanned data into a procedural environment.