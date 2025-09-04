- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (UV)
    
- **Core Function:** Takes an existing UV map and automatically repacks its islands—scaling and moving them to fit as efficiently as possible within the standard 0-1 UV space. This is the procedural equivalent of the "Pack Islands" operator in the UV Editor.
    
- **Key Properties & Settings:**
    
    - **UV (Socket - Input):** The 2D vector field representing the UV map to be packed. This is typically from a Named Attribute node referencing an existing UV map.
        
    - **Selection (Socket - Input):** A boolean face selection. Only the UV islands corresponding to the selected faces will be included in the packing operation.
        
    - **Margin (Socket - Input):** A float that controls the amount of empty space to leave between the packed UV islands.
        
    - **Rotate (Socket - Input):** A boolean. If True, the node is allowed to rotate UV islands to achieve a tighter, more efficient fit.
        
    - **UV (Socket - Output):** The new, repacked UV map.
        
- **Practical Application:** This node is a powerful optimization tool, especially when creating procedural assets from multiple parts. Imagine you are building a procedural animal using a "kitbashing" approach, where you combine a pre-made head, a procedural body, and pre-made legs.
    
    1. **The Problem:** The head, body, and legs all have their own separate UV maps. When you join them, their UV islands will likely be overlapping, making it impossible to texture the creature with a single, unified texture map.
        
    2. **The Goal:** To combine all the UVs into a single, clean, non-overlapping layout.
        
    3. **The Solution:**
        
        - After you Join Geometry to combine all the creature's parts into a single mesh, retrieve their existing (but messy and overlapping) UV maps.
            
        - Feed this combined UV map into the Pack UV Islands node.
            
        - Set a small Margin (e.g., 0.01) to prevent texture bleeding, and enable Rotate for the best packing efficiency.
            
        - The UV output of this node is a brand new, perfectly organized UV layout. All the separate islands for the head, body, and legs have been automatically scaled and arranged to fit together in the 0-1 space without any overlaps.
            
        - You can then use a Store Named Attribute node to save this new layout as your final "UVMap" for texturing.