- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** An all-in-one node that combines the functions of the Translate, Rotate, and Scale nodes into a single, convenient interface. It allows you to move, rotate, and resize an image simultaneously.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **X / Y (Sockets):** Controls the horizontal and vertical **position** of the image. Values are in pixels relative to the image center.
        
    - **Angle (Socket):** Controls the **rotation** in degrees.
        
    - **Scale (Socket):** Controls the uniform **size** of the image. A value of 1.0 is the original size, 0.5 is half size, 2.0 is double size.
        
    - **Filter Type (Property):** The interpolation algorithm used for scaling and rotation (Cubic for best quality, Bilinear for speed, Nearest for pixel art).
        
- **Practical Application:** The Transform node is the workhorse for most animation and placement tasks in the compositor, as it consolidates the most common operations into one place.
    
    - **Molecular (Animating Motion Graphics):** This is its primary use. To make a logo or title "fly in" to the screen:
        
        1. Connect your logo Image to the Transform node.
            
        2. At frame 1, set keyframes for a large Scale (e.g., 3.0), a high Angle (e.g., 180), and an off-screen X/Y position.
            
        3. At your end frame, set keyframes for Scale=1.0, Angle=0, and the final on-screen X/Y position.
            
        4. The result is a dynamic animation where the logo flies in, spinning and scaling down into its final position, all controlled from a single node.
            
    - **Molecular (Picture-in-Picture):** A quick way to create a picture-in-picture effect. Use the Scale slider to shrink your inset image, then use the X and Y sliders to position it in a corner of the frame.
        
    - **Organic (Attaching an Element to a Tracker):** This is a fundamental VFX "molecule."
        
        1. Use a Track Position node to get the X and Y coordinates from a tracker in your footage.
            
        2. Take the element you want to attach (e.g., a lens flare) and feed it into a Transform node.
            
        3. Connect the X and Y outputs from the Track Position node to the X and Y inputs of the Transform node.
            
        4. You may need to use Math (Subtract) nodes in between to offset the coordinates so the element is centered on the tracker. The element will now be perfectly "stuck" to the moving point in your footage.
            
    - **Organic (Creating Feedback Loops/Hall of Mirrors):** By feeding the output of a Transform node back into its own input chain (via a Mix node), you can create fractal-like feedback effects.
        
        1. Start with an image.
            
        2. Use a Transform node to scale it down slightly and move it off-center.
            
        3. Use a Mix node. Connect the original image to the top socket, and the transformed image to the bottom socket.
            
        4. Crucially, connect the output of this Mix node back to the input of the Transform node.
            
        5. The result is an infinite "hall of mirrors" or "Droste effect," where the image contains a smaller, transformed version of itself, infinitely.