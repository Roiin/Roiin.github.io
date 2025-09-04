- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Point
    
- **Core Function:** Converts a point cloud into a mesh that consists only of disconnected vertices. This is the first step in procedurally constructing a new mesh (with edges and faces) from a set of calculated point positions.
    
- **Key Properties & Settings:**
    
    - **Points (Socket - Input):** The source point cloud geometry.
        
    - **Selection (Socket - Input):** A Boolean mask. Only points where this is True will be converted into vertices.
        
    - **Vertices (Socket - Output):** The resulting geometry, which is a mesh containing only loose vertices.
        
- **Practical Application:** This node is a fundamental building block for creating custom mesh topology. Imagine you want to create a constellation by connecting stars (points) to form the shape of an animal.
    
    1. First, you create a point cloud representing the star positions. This could be from a Distribute Points... node or a Points node with manually entered positions.
        
    2. **The Goal:** You need to create edges between specific stars to draw the constellation's shape.
        
    3. **The Problem:** You can't create edges on a point cloud. You first need a mesh.
        
    4. **The Solution:**
        
        - Use the Points to Vertices node. The output is now a mesh object, which is what you need for the next step.
            
        - Now you can use a node like Convex Hull on these vertices. This will generate a mesh that "shrink-wraps" the stars, creating a faceted, crystal-like representation of the animal's shape.
            
    5. Alternatively, for more precise connections, after converting to vertices, you could procedurally create an edge list and use scripting or future nodes to "connect the dots" and build the exact constellation shape. The Points to Vertices node was the non-negotiable first step that changed the data type into something that could have edges and faces.