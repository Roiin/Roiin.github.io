- **Editor:** Logic Node Editor
    
- **Node Group:** Nodes > Geometry
    
- **Core Function:** Sets the value of an input socket within a Geometry Node tree, allowing for real-time changes to the object's mesh.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Node Tree (Socket):** A reference to the Geometry Node tree to modify.
        
    - **Node Name (Socket):** The name of the node within the tree.
        
    - **Socket Name (Selector):** The name of the input socket to change.
        
    - **Value (Socket):** The new data to be assigned to the socket.
        
- **Practical Application:** This is an extremely powerful node for runtime procedural generation. Examples: changing a "Scale" input to make a procedural building grow, modifying a "Density" value to add or remove trees from a forest, or feeding a player's position into the tree to dynamically displace the ground beneath their feet.