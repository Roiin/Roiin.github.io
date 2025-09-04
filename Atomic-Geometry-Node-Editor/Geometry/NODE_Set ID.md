- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Write)
    
- **Core Function:** Sets or creates the id attribute, a stable, persistent integer identifier for each element. Unlike the index, which can change when geometry is altered, the id remains consistent, making it essential for reliable randomization and tracking elements through procedural operations.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The geometry whose id attribute will be set.
        
    - **Selection (Socket - Input):** A Boolean field that acts as a mask. The id will only be set on elements where this is True`.
        
    - **ID (Socket - Input):** An integer field that provides the new id values. By default, this uses the element's Index, which is the most common and effective use case for "freezing" the initial state.
        
    - **Geometry (Socket - Output):** The geometry, now containing the new or update did` attribute.
        
- **Practical Application:** This node is vital for maintaining consistency when parts of your geometry are deleted. Imagine you are procedurally generating a forest on a large grid of points, and you want each tree to have a unique, random size.
    
    - **The Problem:** If you use the Index of each point as the Seed for a Random Value node to control scale, everything looks fine at first. However, if you then delete a circular area of points to create a clearing, the indices of all the points after the clearing will shift. This causes all the remaining trees to suddenly and undesirably change their size.
        
    - **The Solution:**
        
        1. Immediately after creating your initial Grid of points, insert a Set ID node. Leave its ID input unconnected. By default, it will assign the id of each point to be its current index (0, 1, 2, 3...). This effectively "saves" the initial index as a permanent ID.
            
        2. Now, in your Random Value node, use the ID Node as the Seed input, not the Index node.
            
        3. Now you can delete any points you want to create your clearing. A point that was originally index #50 might now be index #40, but its id will still be 50.
            
        4. Because the id is stable, the seed for the random scale never changes for the surviving trees. They all keep their original size, and the forest remains visually consistent.