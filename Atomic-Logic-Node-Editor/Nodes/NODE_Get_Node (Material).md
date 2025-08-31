- **Editor:** Logic Node Editor
    
- **Node Group:** Nodes > Material
    
- **Core Function:** Retrieves a direct reference to a specific node within a material's shader node tree.
    
- **Key Properties & Settings:**
    
    - **Material (Socket):** A material input that specifies which material to search in.
        
    - **Node Name (Socket):** A string input for the name of the shader node to get (e.g., "Principled BSDF", "Emission").
        
    - **Node (Socket):** An output that provides a reference to the found shader node.
        
- **Practical Application:** A foundational node for material manipulation. It is often the first step before using Get Socket Value or Set Socket Value to read or write data to a specific shader node.