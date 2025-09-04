- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Sample)
    
- **Core Function:** For each element, this node searches within the same geometry to find the index of the single closest neighboring element. It is an internal search, ideal for creating self-referential effects.
    
- **Key Properties & Settings:**
    
    - **Position (Socket - Input):** The position from which to start the search for each element. By default, this is the element's own position.
        
    - **Group ID (Socket - Input):** An optional integer field. If used, the search for a nearest neighbor will be restricted to only include elements within the same Group ID.
        
    - **Index (Socket - Output):** The primary output; an integer field containing the index of the closest neighbor found for each element.
        
    - **Has Neighbor (Socket - Output):** A Boolean that is True if a neighbor was found (relevant when using Group ID, ensuring a group has more than one member).
        
- **Practical Application:** This node is perfect for creating "spreading" or "connecting" effects. Imagine you have a field of flowers (instanced on a grid), and a few of them are a magical glowing color. You want this glow to spread to their nearest neighbors.
    
    1. First, you store a custom attribute called "is_glowing" on the grid points before instancing. It's 1.0 for the magical flowers and 0.0 for the rest.
        
    2. Use the Index of Nearest node. For every point, it now knows the index of its closest neighbor.
        
    3. Connect this Index output to a Sample Index node. In the Sample Index node, you tell it to read the "is_glowing" attribute value.
        
    4. The result is that every non-glowing flower now knows if its closest neighbor is glowing. You can use this information in the shader to make it have a subtle, secondary glow. If you were to repeat this process over several frames in a simulation, you could make the magical glow spread across the entire field, one "neighbor" at a time.