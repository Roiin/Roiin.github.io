- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each edge in a mesh, this node outputs a boolean value that is True if the edge is set to 'Smooth' and False if it has been manually marked as 'Sharp'.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Smooth (Socket - Output):** A Boolean field on the Edge domain. True for smooth edges, False for sharp edges.
        
- **Practical Application:** This node is perfect for allowing an artist to guide a procedural effect. Imagine you are creating a procedural system that adds worn, beveled edges to a sci-fi crate. You want most edges to get a wide, soft bevel, but you want a few specific edges to have a tight, sharp bevel for a more detailed look.
    
    1. **The Prep:** The artist goes into Edit Mode on the base crate model and manually marks the few specific edges they want to be tight as 'Sharp'.
        
    2. **The Node Tree:**
        
        - Use the Is Edge Smooth node. The Smooth output gives you a selection for all the non-sharp edges.
            
        - You can invert this selection (using a Boolean Math 'Not' node) to get a selection for only the sharp edges.
            
    3. You can now use these two separate selections to drive two different procedural effects:
        
        - On the 'Smooth' selection, apply a Bevel node with a large Amount and multiple Segments to create a soft, rounded bevel.
            
        - On the 'Sharp' selection, apply a second Bevel node with a very small Amount and only one Segment to create a tight, crisp chamfer.
            
    4. Join the results. The Is Edge Smooth node allowed your single node tree to perform two different operations, intelligently applying the correct bevel type based on the artist's direct, manual input on the mesh.