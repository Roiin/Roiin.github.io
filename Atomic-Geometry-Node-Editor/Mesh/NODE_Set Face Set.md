- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Write)
    
- **Core Function:** Programmatically assigns faces to a specified Face Set. Face Sets are a feature primarily used in Sculpt Mode for quickly creating and isolating editable regions of a mesh. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The mesh geometry whose Face Sets will be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. Only faces where this is True will have their Face Set assigned.
        
    - **Face Set (Socket - Input):** An integer field that provides the ID of the Face Set to which the selected faces will be assigned.
        
    - **Mesh (Socket - Output):** The mesh with the updated Face Set data.
        
- **Practical Application:** This node allows you to create custom tools that procedurally generate masks for sculpting. Imagine you have a complex creature model and you want to quickly create a mask for all the upward-facing surfaces to sculpt on, as if snow had settled on it.
    
    1. **The Tool:** You create a custom "Mask by Normal" tool. The user runs the tool in Sculpt Mode.
        
    2. Inside the tool's node graph, you take the Normal of every face.
        
    3. You use a Vector Math node (Dot Product) to compare each face's normal to a world "up" vector (0, 0, 1).
        
    4. Use a Compare node to create a Boolean Selection for all faces where the dot product is greater than a certain threshold (e.g., 0.5), meaning they are generally facing upwards.
        
    5. Feed this Selection into the Set Face Set node. For the Face Set input, provide a constant integer, for example, 1.
        
    6. **The Result:** After running the tool, a new Face Set is created on the creature. The user can now simply hover over any upward-facing part of the model and press a hotkey (like H) to hide everything else, instantly isolating the areas for sculpting scales, fur, or other details that would only appear on the top surfaces. The tool has transformed a complex procedural selection into a simple, artist-friendly sculpting mask.