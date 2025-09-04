- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Outputs a single, user-defined numerical value (floating-point).
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Value (Property):** A numeric field directly on the node to set the desired decimal value.
        
    - **Value (Socket - Output):** The specified numerical value.
        
- **Practical Application:** This is one of the most common nodes for parameter control. For instance, when creating a procedural landscape, you might use a Noise Texture node to displace the geometry. You can connect a Value node to the Scale input of the Noise Texture. This gives you a single, simple slider in your node tree to control the overall size and frequency of the terrain features, making it easy to art-direct the final look.