- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Grease Pencil (Operations)
    
- **Core Function:** Flattens multiple Grease Pencil layers into a single layer based on a shared name or a procedural Group ID.
    
- **Key Properties & Settings:**
    
    - **Grease Pencil (Socket - Input):** The source Grease Pencil geometry containing multiple layers.
        
    - **Selection (Socket - Input):** A boolean mask that acts as a filter, allowing the merge operation to only consider a subset of all layers.
        
    - **Group ID (Socket - Input):** In 'By Group ID' mode, this integer field determines which layers get merged. All layers with the same ID will be combined.
        
    - **Mode (Property):** The core control for the merging logic:
        
        - **By Name:** Automatically finds and merges all layers that share the exact same name.
            
        - **By Group ID:** Merges layers based on the integer provided to the Group ID input socket, allowing for more complex, procedural grouping.
            
    - **Grease Pencil (Socket - Output):** The modified Grease Pencil geometry, where the specified layers have been combined.
        
- **Practical Application:** The 'By Group ID' mode is extremely powerful for procedural organization. Imagine you are creating a 2D animation of a forest with many trees. Each tree is drawn with two layers: "Tree_Trunk" and "Tree_Leaves".
    
    1. **The Problem:** You have 50 layers in your scene ("Tree_Trunk_1", "Tree_Leaves_1", "Tree_Trunk_2", etc.), making it very difficult to manage. You want to combine all the trunks into one layer and all the leaves into another.
        
    2. **The Solution:** Use the Merge Layers node in 'By Group ID' mode.
        
        - First, you need to generate a Group ID. You can create a boolean selection for all layers whose name contains "Trunk" and use a Switch node to give them a Group ID of 1. Give all other layers (the leaves) a Group ID of 2.
            
        - Feed this procedural Group ID into the Merge Layers node.
            
    3. The node will now process your file and perform two merges:
        
        - All layers with ID 1 (the trunks) will be flattened into a single new layer.
            
        - All layers with ID 2 (the leaves) will be flattened into another new layer.
            
    4. You have instantly reorganized a scene with 50 layers into just two, making it vastly easier to apply effects, change colors, or manage the animation for all trunks or all leaves simultaneously.