- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Import)
    
- **Core Function:** Loads all volumetric grids from an external .vdb file and makes them available as a single Volume object within the node tree.
    
- **Key Properties & Settings:**
    
    - **Path (Socket - Input):** A string specifying the file path to the .vdb file.
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Volume (Socket - Output):** The resulting Volume geometry containing the data from the imported file.
        
- **Practical Application:** This is essential for integrating high-quality simulations. For instance, you could import a complex smoke simulation saved as smoke_plume.vdb. While the volume is primarily rendered with a volumetric shader, you can also use its data procedurally. By connecting the Volume output to a Sample Volume node, you can read the smoke's density at any point in space. This density value could then be used to drive the scale of dust motes instanced inside the smoke, making them larger in denser areas and smaller or non-existent in thinner areas, adding another layer of realism to the effect.