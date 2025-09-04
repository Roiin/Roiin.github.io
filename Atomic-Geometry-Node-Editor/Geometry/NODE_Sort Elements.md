- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Reorganizes the internal order of geometry elements by re-assigning their indices based on a given "weight" value. This allows you to sort elements by criteria like distance, size, or a random value.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The geometry whose elements are to be sorted.
        
    - **Selection (Socket - Input):** A boolean mask. Only elements where this is True will be included in the sort; unselected elements will retain their original indices.
        
    - **Group ID (Socket - Input):** An integer field. If used, elements are sorted independently within each group ID, but the groups themselves are not reordered.
        
    - **Sort Weight (Socket - Input):** The critical input. This is a float or integer field that provides the value to sort by. Elements with lower weight values will be given lower indices (i.e., they will come first in the new order).
        
    - **Domain (Property):** The type of element to sort (Point, Edge, Face, Spline, or Instance).
        
    - **Geometry (Socket - Output):** The geometry with its elements re-indexed according to the sort weights.
        
- **Practical Application:** This node is perfect for creating ordered effects, like a magical particle trail that connects points in a logical sequence.
    
    1. First, create a cloud of "magic dust" particles by distributing points in a volume.
        
    2. Next, add an Empty object to your scene to act as a "controller" or "start point" for the trail.
        
    3. **The Goal:** You want to draw a single, continuous curve that snakes through the dust cloud, connecting the particles in order of their proximity to the Empty.
        
    4. Use the Sort Elements node on your particle cloud. For the Sort Weight input, calculate the Distance from each particle's Position to the Location of your Empty controller.
        
    5. The output of this node is the same cloud of points, but now they are re-indexed. Point #0 is the particle closest to the Empty, point #1 is the second closest, and so on.
        
    6. Finally, feed this sorted point cloud into a Points to Curves node. Because the points are now in a logical order, the node will draw a single, elegant curve that starts near the Empty and intelligently weaves its way through the entire particle system. This creates a far more intentional and visually appealing effect than connecting random points.