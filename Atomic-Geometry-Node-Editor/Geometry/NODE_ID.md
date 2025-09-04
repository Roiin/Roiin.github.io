- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Outputs the stable, persistent id attribute for each element. This identifier remains consistent even if the geometry is modified and element indices change. If no id attribute has been set, this node will output the element's index instead.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **ID (Socket - Output):** An integer field representing the unique and stable identifier of each element.
        
- **Practical Application:** This node is essential for maintaining consistency in procedural setups where geometry is deleted or reordered. For example, imagine scattering trees on a grid and giving each a random rotation and scale based on a seed value.
    
    - If you use the Index node as the seed, and then delete some of the grid points, the indices of the remaining points will shift, causing the rotation and scale of all the trees to change unpredictably.
        
    - By first using a Set ID node on the initial grid, and then using this ID node as the seed for your randomization, you can delete points freely. The surviving points will retain their original id, and therefore their unique rotation and scale will remain stable and unchanged, which is the desired behavior.