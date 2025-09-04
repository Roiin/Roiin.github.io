- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Reads the "direction map" output from a Shortest Edge Paths node and creates a Boolean selection for all the edges that make up the paths from a set of Start Vertices to their calculated endpoints.
    
- **Key Properties & Settings:**
    
    - **Start Vertices (Socket - Input):** A Boolean selection identifying the vertices where the path tracing should begin.
        
    - **Next Vertex Index (Socket - Input):** This is the critical input. It should be connected directly to the Next Vertex Index output of a Shortest Edge Paths node.
        
    - **Selection (Socket - Output):** A Boolean field on the Edge domain. It is True for every edge that is part of a traced path.
        
- **Practical Application:** This node is perfect for procedurally creating glowing "circuit board" traces or "magical runes" that spread across a surface.
    
    1. Start with a complex mesh, like a piece of sci-fi armor.
        
    2. Set up a Shortest Edge Paths node. Select a few key vertices as the End Vertex "power sources". Use the edge length as the Edge Cost.
        
    3. Select a different set of vertices as the Start Vertices "terminals".
        
    4. **The Goal:** You want to make the shortest paths between these terminals and power sources glow.
        
    5. Use the Edge Paths to Selection node. Connect the Start Vertices and the Next Vertex Index from your path calculation.
        
    6. The Selection output is now a Boolean mask that highlights only the edges forming the circuit traces.
        
    7. Use a Store Named Attribute node to save this edge selection as an attribute (e.g., "is_circuit").
        
    8. In the Shader Editor, you can use an Attribute node to read "is_circuit". This gives you a factor that is 1.0 on the circuit edges and 0.0 everywhere else. You can plug this directly into the Emission Strength of your material.
        
    9. The result is a complex network of glowing lines that intelligently follows the contours of your armor, all generated procedurally.