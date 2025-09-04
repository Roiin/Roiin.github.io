- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For every vertex in a mesh, this node calculates the most efficient path along the mesh's edges to reach the nearest of a designated set of End Vertex points. The "efficiency" of a path is determined by the Edge Cost. The node's output is not a visible path itself, but rather a set of "directions"—for each vertex, it tells you which vertex is the next step on the path.
    
- **Key Properties & Settings:**
    
    - **End Vertex (Socket - Input):** A Boolean selection identifying the destination or "root" vertices. All paths will lead towards these points.
        
    - **Edge Cost (Socket - Input):** A float field on the Edge domain that defines the "cost" of traversing each edge. The node finds the path with the lowest total cost. A common input here is the actual length of each edge.
        
    - **Next Vertex Index (Socket - Output):** The primary output. For each vertex, this provides the index of the next vertex along the shortest path to an endpoint. This is the "direction map" that other nodes can follow.
        
    - **Total Cost (Socket - Output):** For each vertex, this provides the total remaining cost to reach the nearest endpoint. This is effectively a distance field that radiates out from the end vertices.
        
- **Practical Application:** This node is perfect for generating organic, vein-like structures that spread across a creature's skin.
    
    1. **The Goal:** You want to procedurally generate a network of glowing veins on an animal, all originating from a central point on its chest.
        
    2. **The Setup:**
        
        - First, select a single vertex on your animal's chest mesh. This will be your End Vertex selection.
            
        - To make the veins follow the surface realistically, you need to set the Edge Cost to be the actual length of each edge. You can calculate this with an Edge Vertices node and a Vector Math node set to 'Distance'.
            
    3. **The Problem:** The Shortest Edge Paths node's output is just data, not a visible object.
        
    4. **The Solution:** You need another node to interpret this data. Use the Edge Paths to Curves node. This node is specifically designed to read the Next Vertex Index map. It traces the paths from various "start" points (which you can define, for example, on the animal's hands and feet) back to the End Vertex on the chest.
        
    5. **The Result:** The Edge Paths to Curves node outputs a set of curve objects that perfectly follow the shortest path along the animal's skin from its extremities to its heart. You can then use Curve to Mesh on these curves to give them thickness and a glowing material, creating a stunning and highly realistic procedural effect.