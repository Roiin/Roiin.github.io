- **Editor:** Compositor Node Editor
    
- **Node Group:** Output
    
- **Core Function:** Saves the image data from any point in the node tree to a separate file or image sequence on your hard drive during the rendering process. It acts as an additional, independent render output, separate from the final Composite node.
    
- **Key Properties & Settings:**
    
    - **Base Path (Property):** The directory/folder where the files will be saved.
        
    - **File Subpath (Property):** The name of the output file. The final output path is a combination of the Base Path and this name (e.g., C:\renders\ + MyRender_Pass.exr).
        
    - **File Format (Property):** Allows you to select the output format (e.g., OpenEXR, PNG, TIFF) and its settings (color depth, compression), which can be different from the main render output settings.
        
    - **Add Input (Property):** This is a key feature. Clicking this button adds a new input socket to the node, allowing you to save multiple image streams into a single multi-layer EXR file.
        
    - **Image (Socket):** The default input socket. Whatever is connected here will be saved. Additional sockets can be added.
        
- **Practical Application:** This node is essential for breaking a complex render into manageable parts, creating utility passes, and optimizing your workflow. It allows you to save "milestones" in your node graph.
    
    - **Molecular (Saving Utility Passes):** Imagine you've created a complex procedural matte for heat distortion using several Texture and Math nodes. You don't want to re-calculate this every time you tweak the final color grade. You can connect the output of your matte generation into a File Output node and render it once as a black-and-white image sequence. In subsequent renders, you can disable that part of the node tree and simply bring the pre-rendered matte back in with an Image node, saving significant processing time.
        
    - **Molecular (Simultaneous Beauty and Clay Render):** You need to deliver both the final colored render and a simple "clay" render for review.
        
        1. Connect your final, color-corrected image stream to the main Composite node.
            
        2. Connect your raw Render Layers Image output (before color correction) to a File Output node.
            
        3. When you render, Blender will save both the final colored image (from Composite) and the clean, raw image (from File Output) at the same time, in a single render pass.
            
    - **Organic (Creating a Custom Multi-Layer EXR):** This is the node's most powerful professional use. In a large VFX shot, you might have separate renders for the foreground character, the mid-ground vehicle, and the background environment.
        
        1. Add a File Output node and set the format to OpenEXR with Multi-layer enabled.
            
        2. Use the Add Input button to create three input sockets. Name them Foreground, Midground, and Background.
            
        3. Pipe the final composite of each element into its respective socket.
            
        4. When you render, this node will generate a single EXR file per frame that contains all three elements as separate layers. A final compositing artist can then load this single file into another application (or another Blender scene) and have full, independent control over the color, position, and effects for each layer, providing maximum flexibility in the final stages of production.