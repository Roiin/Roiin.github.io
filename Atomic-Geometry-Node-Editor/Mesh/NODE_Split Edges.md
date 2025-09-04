- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Splits a mesh's edges based on a selection, duplicating the vertices along those edges. This effectively "tears" the mesh apart, separating faces that were once connected. This is the procedural equivalent of the Edge Split modifier.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be split.
        
    - **Selection (Socket - Input):** A Boolean field on the Edge domain. Edges where this is True will be split.
        
    - **Mesh (Socket - Output):** The mesh with its selected edges split. Although it may look the same, it is now made of multiple, disconnected mesh islands.
        
- **Practical Application:** This node is essential for creating a "disassemble" or "explosion" animation effect for a mechanical creature.
    
    1. Start with a complete, manifold model of a robotic animal.
        
    2. **The Goal:** You want the animal to break apart into its constituent armor plates and fly outwards.
        
    3. First, you need to define the seams. You can do this procedurally by selecting edges with a sharp angle using the Edge Angle node, or by using edges that were manually marked as 'Sharp'. Feed this Boolean edge selection into the Selection input of the Split Edges node.
        
    4. The output of this node is a mesh that looks identical, but is now composed of dozens of separate mesh islands (one for each armor plate).
        
    5. Now that the plates are separate islands, you can use a Scale Elements node (with the Domain set to 'Face'). For the Center input, you can use the center of each mesh island (calculated with an Attribute Statistic node grouped by Mesh Island index).
        
    6. By animating the Scale factor of this Scale Elements node, you can make the individual plates shrink, or by using a Translate node driven by the island centers, you can make them fly apart. The Split Edges node was the critical step that allowed you to break the single mesh into movable parts.