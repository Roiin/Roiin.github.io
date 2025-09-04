- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Extracts metadata and properties, such as dimensions and frame count, from a specified image or video file.
    
- **Key Properties & Settings:**
    
    - **Image (Socket - Input):** The source image or video data-block to be analyzed.
        
    
    - **Frame (Socket - Input):** The specific frame number from which to get information.
        
    - **Width (Socket - Output):** The image's width in pixels at the specified frame.
        
    - **Height (Socket - Output):** The image's height in pixels at the specified frame.
        
    - **Has Alpha (Socket - Output):** A Boolean that is True if the image contains transparency data.
        
    - **Frame Count (Socket - Output):** The total number of frames in the image sequence or video.
        
    - **FPS (Socket - Output):** The playback speed in frames per second.
        
- **Practical Application:** This node is perfect for automatically creating a plane that matches an image's aspect ratio. You can create a Grid primitive and feed its Size input with the image's dimensions. To keep the plane a manageable size, you can divide the Width by the Height using a Math node to get the aspect ratio, then use that value to drive the grid's X-size while keeping its Y-size at 1. This ensures that no matter which image you load, the procedural plane will never be distorted, which is ideal for creating image display panels.