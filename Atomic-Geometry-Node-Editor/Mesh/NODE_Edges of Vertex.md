- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For a given vertex, this node finds all the edges connected to it, sorts them based on a weight, and then outputs the index of a single edge from that sorted list. It's a tool for asking, "Of all the edges connected to this point, which one is the longest/shortest/most vertical?"
    
- **Key Properties & Settings:**
    
    - **Vertex Index (Socket - Input):** The index of the vertex to be queried.
        
    - **Weights (Socket - Input):** A field evaluated on the Edge domain, used to sort the edges connected to the vertex.
        
    - **Sort Index (Socket - Input):** An integer that picks an edge from the sorted list (0 is the one with the lowest weight).
        
    - **Edge Index (Socket - Output):** The primary output; the global index of the selected edge.
        
    - **Total (Socket - Output):** The total number of edges connected to the vertex.
        
- **Practical Application:** This node is perfect for creating procedurally oriented details. Imagine you have a mesh of an animal's crystal shell, and at every vertex, you want to grow a single, larger crystal shard that aligns with the "most vertical" edge connected to that vertex.
    
    1. **The Goal:** Instance and align a crystal shard at each vertex based on local topology.
        
    2. **The Weights:** First, you need a "verticality score" for every edge. You can get the direction of each edge using Edge Vertices and subtracting their positions. Then, take the Dot Product of this direction with a pure "up" vector (0, 0, 1). The absolute value of this gives you a score from 0 (horizontal) to 1 (vertical). To sort so the most vertical edge is first, you need the lowest weight, so you use 1 - score as your Weights input.
        
    3. **The Query:** Use the Edges of Vertex node. Feed your calculated 1 - score into the Weights input. Set the Sort Index to 0 to pick the edge with the lowest weight (which is the most vertical one).
        
    4. The Edge Index output now gives you the index of the single most vertical edge at each vertex.
        
    5. **The Alignment:** You can now use a Sample Index node (on the Edge domain) to get the direction of this specific edge. Use this direction vector with an Align Euler to Vector node to create the correct rotation for your crystal shard instances.
        
    6. The result is a creature covered in crystal growths, where each growth is intelligently aligned to the most prominent vertical feature of the local geometry, creating a very structured and visually appealing organic pattern.