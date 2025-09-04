- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For any given face corner, this node identifies the face that the corner belongs to and outputs that face's index.
    
- **Key Properties & Settings:**
    
    - **Corner Index (Socket - Input):** The index of the face corner to be queried.
        
    - **Face Index (Socket - Output):** The primary output; the global index of the face that contains the specified corner.
        
    - **Index in Face (Socket - Output):** The corner's local index within its face (e.g., a value from 0 to 3 for a quad).
        
- **Practical Application:** This node is often used as a bridge after a selection has been made on the corner domain. Imagine you are creating a procedural "damage" system for an animal's armor, and the damage originates from specific points.
    
    1. You have a point cloud of "impact points" representing where the armor has been hit.
        
    2. Using a Geometry Proximity node, you find the nearest face corner on the armor for each impact point. You now have a selection of face corners that have been "hit".
        
    3. **The Goal:** You want to apply a "dented" material to the entire face that was hit, not just the single corner.
        
    4. **The Problem:** Your selection is on the Face Corner domain, but you need a selection on the Face domain to use with a Set Material node.
        
    5. **The Solution:** Use the Face of Corner node.
        
        - The input is your selection of "hit" corners.
            
        - The Face Index output gives you the index of the corresponding face for each of those hit corners.
            
    6. You now have a list of face indices. You can use this to build a new Boolean selection on the Face domain, which you can then feed into a Set Material node to apply your "dented" material. The Face of Corner node was the essential link that allowed you to promote a selection from a single corner to the entire face it belongs to.