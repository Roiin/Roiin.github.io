- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** Resizes an image, making it larger or smaller. It offers various modes for handling different aspect ratios and coordinate spaces.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be resized.
        
    - **Space (Property):** The coordinate system for scaling.
        
        - Relative: The most common mode. X and Y sockets control scaling as a percentage of the original size (e.g., 0.5 is 50%, 2.0 is 200%).
            
        - Absolute: X and Y sockets control the final size in absolute pixels.
            
        - Render Size: Automatically resizes the image to match the project's final render dimensions, with options for handling aspect ratio differences.
            
    - **X / Y (Sockets):** The scaling factors. If you want to scale uniformly, these values must be the same.
        
    - **Offset X / Y (Sockets):** An additional control available in Render Size mode to shift the image within the new frame.
        
    - **Filter Type (Property):** The interpolation algorithm.
        
        - Cubic: Highest quality for upscaling, preserves detail.
            
        - Bilinear: Good all-around quality and speed.
            
        - Nearest: No smoothing. For pixel art or deliberate blockiness.
            
- **Practical Application:** Scaling is a core utility for matching resolutions, creating motion, and fixing stabilization artifacts.
    
    - **Molecular (Matching Resolutions):** This is a critical technical use. If you are compositing a 4K render over a 1080p background plate, you must scale one to match the other before they can be combined correctly with an Alpha Over node. The Render Size mode with Fit or Crop is perfect for this, automatically conforming one image to the project's dimensions.
        
    - **Molecular (Animating Zooms):** By animating the X and Y values in Relative mode, you can create a "zoom in" (values increasing from 1.0) or "zoom out" (values decreasing from 1.0) effect.
        
    - **Organic (Fixing Stabilization Borders):** When you use the Stabilize 2D node, it creates black, empty borders as the image shifts to stay steady. The solution is a "molecule" made of Stabilize 2D followed by Scale.
        
        1. After stabilizing your footage, add a Scale node.
            
        2. Set it to Relative mode and increase the X and Y values slightly (e.g., to 1.1).
            
        3. This "punches in" on the footage just enough to hide the moving black edges, giving you a clean, steady shot that fills the frame.
            
    - **Organic (Picture-in-Picture Effect):**
        
        1. Take the video clip you want to be the "inset" picture.
            
        2. Use a Scale node to shrink it down (e.g., X/Y of 0.25).
            
        3. Use a Transform or Translate node to position this smaller image in a corner of the screen.
            
        4. Alpha Over this result on top of your main background footage.