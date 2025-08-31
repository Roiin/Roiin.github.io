- **Editor:** Logic Node Editor
    
- **Node Group:** Nodes > Material
    
- **Core Function:** Retrieves the value from an input socket of a specific node within a material's shader node tree.
    
- **Key Properties & Settings:**
    
    - **Material (Socket):** The material to query.
        
    - **Node Name (Socket):** The name of the shader node containing the socket.
        
    - **Socket Name (Selector):** A dropdown/text field to specify the name of the input socket (e.g., "Base Color", "Roughness", "Emission Strength").
        
    - **Value (Socket):** The data output, providing the value of the requested socket.
        
- **Practical Application:** Used to read material properties at runtime. For example, reading the "Emission Strength" of a material to determine if an object is currently glowing.