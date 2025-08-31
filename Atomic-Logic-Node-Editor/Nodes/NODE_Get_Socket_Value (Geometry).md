- **Editor:** Logic Node Editor
    
- **Node Group:** Nodes > Geometry
    
- **Core Function:** Retrieves the value from an input socket within a Geometry Node tree.
    
- **Key Properties & Settings:**
    
    - **Node Tree (Socket):** A reference to the Geometry Node tree data-block.
        
    - **Node Name (Socket):** A string input for the name of the node within the tree (e.g., a "Group Input" node).
        
    - **Socket Name (Selector):** The name of the input socket to read from.
        
    - **Value (Socket):** The data output, providing the value of the requested socket.
        
- **Practical Application:** Reading the current state of a procedural mesh. For example, getting the current "Seed" value of a procedural generation setup or reading the "Scale" input that controls the size of instanced objects.