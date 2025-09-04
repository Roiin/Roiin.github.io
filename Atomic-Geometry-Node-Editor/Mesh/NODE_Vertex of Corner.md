- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For any given face corner, this node identifies the vertex that the corner is associated with and outputs that vertex's index.
    
- **Key Properties & Settings:**
    
    - **Corner Index (Socket - Input):** The index of the face corner to be queried.
        
    - **Vertex Index (Socket - Output):** The primary output; the global index of the vertex that the corner is "at".
        
- **Practical Application:** This node is crucial when you need to transfer attributes from face corners (which can hold unique data like UVs or custom normals per-face) to the vertices they share. Imagine you have a creature with custom-painted vertex colors, but an operation has stored a new, important color value on the face corner domain. You want to average all the corner colors at each vertex to create a final, blended vertex color.
    
    1. You have a color attribute stored on the Face Corner domain.
        
    2. **The Goal:** To create a new color attribute on the Point (Vertex) domain that is the average of all the corner colors meeting at that vertex.
        
    3. **The Problem:** You can't directly average the corner colors because you don't know which corners belong to which vertex.
        
    4. **The Solution:**
        
        - First, use the Accumulate Field node. You want to sum the color values from the corners. The Group ID for this accumulation is the Vertex Index provided by the Vertex of Corner node. This tells the Accumulate node to create a separate sum for each group of corners that share the same vertex.
            
        - You will get a Total sum of the colors for each vertex.
            
        - You also need to know how many corners are at each vertex. The Group Size output of the Accumulate node gives you this count.
            
    5. Finally, divide the Total color sum by the Group Size (using a Vector Math 'Divide' node).
        
    6. The result is a new color attribute on the Point domain that is a perfect, blended average of all the surrounding corner colors. The Vertex of Corner node was the essential key that provided the grouping information needed for the accumulation to work correctly.