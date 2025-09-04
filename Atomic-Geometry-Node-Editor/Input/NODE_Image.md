- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Provides a direct reference to an image datablock, making it accessible within the node tree for texture-based operations.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Image Data-Block (Property):** A data-block selector to choose an existing image or to load a new one from a file.
        
    - **Image (Socket - Output):** The selected image data, ready to be connected to other nodes that can process image information.
        
- **Practical Application:** This is the primary way to introduce textures into a procedural workflow. It can be connected to a Sample Texture node to use the image's color or alpha values to control attributes like instance density, geometry scale, or displacement, effectively allowing an artist to "paint" procedural effects onto a surface.