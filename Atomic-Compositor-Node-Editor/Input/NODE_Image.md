- **Editor:** Compositor Node Editor
    
- **Node Group:** Input
    
- **Core Function:** Loads an external media file—such as a still image, an image sequence, or a movie file—into the compositor's node tree. It is the primary gateway for bringing pre-existing visual elements into your composition.
    
- **Key Properties & Settings:**
    
    - **Image Data-Block (Property):** The file browser used to select the image or the first frame of a sequence.
        
    - **Color Space (Property):** Defines the color space of the input file (e.g., sRGB for standard photos/videos, Linear for EXR renders). Setting this correctly is crucial for proper color management.
        
    - **Sequence (Property Checkbox):** Must be enabled when loading an image sequence (e.g., frame_0001.png, frame_0002.png, etc.).
        
    - **Frames (Property):** Sets the number of frames to use from the sequence.
        
    - **Start Frame (Property):** Defines the project frame on which the sequence will begin playing.
        
    - **Image (Socket):** Outputs the standard RGBA color information of the media.
        
    - **Alpha (Socket):** Outputs the alpha (transparency) channel of the media, if one exists.
        
    - **(Additional Sockets):** If a multi-layer format like an OpenEXR file is loaded, additional sockets will appear for each layer (e.g., Depth, Normal, AO), allowing direct access to render passes saved within the single file.
        
- **Practical Application:** This node is fundamental for combining CG with other visual elements.
    
    - **Molecular (Background Plate):** This is its most common use. Load a photograph of a sky or a city street. Use an Alpha Over node to place your 3D render (from the Render Layers node) on top of this background image, integrating your CG into a real-world setting.
        
    - **Molecular (Texture Overlay):** To break the "perfectly clean" CG look, load a subtle grunge texture or a film grain image. Use a Mix node set to Overlay or Soft Light with a very low factor to blend this texture over your final render. This adds a layer of realism and organic imperfection.
        
    - **Molecular (Lens Dirt & Flares):** Load a high-resolution image of a lens flare or a smudge on a black background. Use a Mix node set to Add or Screen to composite this over your shot. This simulates camera imperfections and can dramatically increase the perceived realism and cinematic quality of the final image.
        
    - **Organic (VFX Pipeline with Multi-Layer EXRs):** In a professional workflow, a 3D artist might render a complex character to a single multi-layer EXR file. A compositing artist can then load this one file using the Image node. They instantly gain access to the Beauty, Depth, Object ID, and other passes through the node's extra sockets. They can then perform complex depth of field, object-specific color corrections, and relighting all from this single node without needing the original 3D scene, creating an efficient and non-destructive post-production pipeline.