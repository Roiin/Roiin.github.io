- **Editor:** Compositor Node Editor
    
- **Node Group:** Input
    
- **Core Function:** Imports video footage from Blender's Movie Clip Editor, acting as the primary bridge for live-action plates and providing direct access to motion tracking and stabilization data.
    
- **Key Properties & Settings:**
    
    - **Movie Clip Data-Block (Property):** The menu to select the video clip that has been loaded and potentially tracked or stabilized in the Movie Clip Editor.
        
    - **Color Space (Property):** Defines the color space of the input video (e.g., sRGB/Rec. 709 for most standard footage). Critical for correct color integration.
        
    - **Image (Socket):** Outputs the color information for the current frame of the video.
        
    - **Alpha (Socket):** Outputs the alpha channel, if the video format supports one.
        
    - **Offset X/Y (Socket):** Outputs the positional data from a 2D track, representing the tracker's movement across the frame.
        
    - **Scale (Socket):** Outputs the scale data from a 2D track, representing changes in size (e.g., if the tracked object moves closer or further from the camera).
        
    - **Angle (Socket):** Outputs the rotational data from a 2D track that has rotation tracking enabled.
        
- **Practical Application:** This node is the foundation for marrying the real world with the digital world. Its power lies in using the tracking data outputs to control other elements.
    
    - **Molecular (Live-Action Plate):** At its simplest, the Image output is used as the background plate. You would use an Alpha Over node to composite your Render Layers (your CG elements) on top of this live-action footage.
        
    - **Organic (Screen Replacement & Set Extension):** This is a classic VFX task. Imagine you filmed an actor holding a smartphone with a blank green screen.
        
        1. In the Movie Clip Editor, you perform a "Corner Pin" track on the four corners of the screen.
            
        2. In the compositor, you bring in the footage with the Movie Clip node.
            
        3. You then add an Image node with the new screen content you want to display.
            
        4. You connect this new screen image to a Corner Pin node and use the tracking data from your footage to drive the pin positions. The result is a new screen that is perfectly "stuck" to the moving phone in the actor's hand.
            
    - **Organic (Integrating Motion Graphics):** You want to add a text title that looks like it's painted on a wall in your video.
        
        1. In the Movie Clip Editor, create a 2D track that follows a specific point on the wall.
            
        2. In the compositor, bring in your footage. Create your text using a Text node.
            
        3. Use a Transform node to position your text. Drive the X and Y sockets of the Transform node with the Offset X and Offset Y outputs from the Movie Clip node's track. The text will now move perfectly with the camera shake, appearing locked to the wall.
            
    - **Organic (Professional VFX Stabilization Workflow):** For seamless integration, you often stabilize the footage first.
        
        1. In the Movie Clip Editor, track a feature and apply 2D stabilization. The Image output of the Movie Clip node will now be a rock-steady version of your footage.
            
        2. Composite your CG element (which is also perfectly steady) on top of this stabilized plate.
            
        3. At the very end of your node tree, add a final Transform node. Drive this node with the same tracking data used for stabilization, but inverted. This re-introduces the original camera shake to the entire composite, ensuring your CG element and the live-action footage share the exact same motion characteristics for a flawless final result.