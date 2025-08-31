
- **Editor:** Logic Node Editor
    
- **Node Group:** Nodes > Material
    
- **Core Function:** Controls the playback of an animated texture or a sequence of images within a material (e.g., an Image Sequence node).
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** A boolean input; the sequence only plays/updates when this is True.
        
    - **Material (Socket):** The material containing the animated texture.
        
    - **Node Name (Socket):** The name of the Image Texture node that is set to a sequence.
        
    - **On Start / Running / On Finish (Sockets):** Flow control outputs that pulse at the beginning, during, and at the end of the sequence playback.
        
    - **Current Frame (Socket):** A float output of the current frame in the image sequence.
        
- **Practical Application:** Used for creating animated effects like a flickering TV screen, a magical portal with swirling textures, or animated character portraits in a UI.