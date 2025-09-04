- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For any given face corner, this node identifies the two edges that form it, providing the index of the "next" edge and the "previous" edge in that face's vertex loop.
    
- **Key Properties & Settings:**
    
    - **Corner Index (Socket - Input):** The index of the face corner to be queried.
        
    - **Next Edge Index (Socket - Output):** The index of the edge that follows the corner in the face's winding order.
        
    - **Previous Edge Index (Socket - Output):** The index of the edge that precedes the corner in the face's winding order.
        
- **Practical Application:** This node is a building block for advanced procedural selections and attribute transfers. Imagine you have a mesh representing the scales of a lizard, and you have a float attribute stored on the edges that represents the "thickness" of the scale's border. You want to transfer this thickness value to the corners.
    
    1. **The Goal:** You need to calculate the average thickness of the two edges that meet at each corner to determine how "thick" that corner should be.
        
    2. Use the Edges of Corner node. For every corner, it gives you the indices of the two edges that form it.
        
    3. Use two Sample Index nodes (with the Domain set to 'Edge'):
        
        - The first Sample Index node uses the Next Edge Index to look up the "thickness" attribute of the next edge.
            
        - The second Sample Index node uses the Previous Edge Index to look up the "thickness" attribute of the previous edge.
            
    4. You now have two float values for each corner. Use a Math node set to 'Add', and then another set to 'Divide' by 2, to calculate their average.
        
    5. The result is a new float field on the corner domain that represents the average border thickness at that specific point. This new attribute could be used, for example, to control the scale of a small spike instanced at each corner, making the spikes larger at thicker parts of the scale's border.