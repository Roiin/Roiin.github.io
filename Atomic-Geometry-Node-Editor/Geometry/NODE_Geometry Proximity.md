- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Sample)
    
- **Core Function:** For a set of source positions, this node finds the nearest point on a separate target geometry and outputs the location of that nearest point as well as the distance to it.
    
- **Key Properties & Settings:**
    
    - **Target (Socket - Input):** The geometry that will be searched against.
        
    - **Source Position (Socket - Input):** A field of positions that are searching from. Typically, this is the Position node of the object the modifier is on.
        
    - **Target Element (Property):** Defines what part of the target geometry to measure against:
        
        - **Points:** Finds the closest vertex. Fastest method.
            
        - **Edges:** Finds the closest point along any edge.
            
        - **Faces:** Finds the closest point on the surface of any face. Most precise for solid objects.
            
    - **Closest Position (Socket - Output):** A vector field representing the location of the nearest point found on the target geometry.
        
    - **Distance (Socket - Output):** A float field representing the calculated distance from the source position to the closest position on the target.
        
- **Practical Application:** This node is perfect for creating environment-aware effects. Imagine you want to create moss that grows on a tree trunk, but only on the side that is close to a damp, stone wall.
    
    1. On your tree object, use an Object Info node to bring in the stone wall as the Target geometry for the Geometry Proximity node.
        
    2. Use the tree's own Position node as the Source Position. The node now calculates, for every point on the tree, its distance to the wall.
        
    3. Take the Distance output and connect it to a Map Range node. You can map the distance (e.g., from 0 to 2 meters) to a new range (from 1 to 0). This creates a smooth falloff gradient.
        
    4. This gradient is a perfect density mask. Use it to drive a Distribute Points on Faces node to scatter moss particles. The result is that moss grows thickly on the parts of the tree trunk touching or near the wall, and elegantly fades away as the distance increases.