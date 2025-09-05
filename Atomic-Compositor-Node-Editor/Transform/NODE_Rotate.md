- **Editor:** Compositor Node Editor
- **Node Group:** Transform
    
- **Core Function:** Rotates an image around a central pivot point.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Angle (Socket):** The amount of rotation in degrees. Positive values rotate clockwise. This socket is animatable.
        
    - **Center X / Y (Sockets):** The coordinates of the pivot point for the rotation. The default (0.5, 0.5) is the exact center of the image.
        
    - **Filter Type (Property):** The interpolation algorithm used for resampling the image after rotation.
        
        - Cubic: The highest quality, best for preserving detail in photos and complex images.
            
        - Bilinear: A good balance of quality and speed.
            
        - Nearest: The fastest, but produces blocky, pixelated results. Only useful for specific retro/pixel art styles.
            
- **Practical Application:** A fundamental tool for correcting orientation, creating motion, and building more complex rotational effects.
    
    - **Molecular (Dutch Angle / Camera Shake):** To add a subtle sense of unease or instability to a shot, you can add a Rotate node and set the Angle to a small value (e.g., 5 to 15 degrees). For camera shake, you can apply a noise modifier to the Angle property in the Graph Editor, making the image jitter randomly.
        
    - **Molecular (Spinning Transitions):** By animating the Angle from 0 to 360 (or higher), you can create a simple spinning transition. This is often combined with a Transform (Scale) node to make the image also zoom in or out as it spins.
        
    - **Organic (Creating Radial Arrays):** This is a powerful motion graphics "organism." To create a circle of objects (like the numbers on a clock face):
        
        1. Create your element (e.g., a number "12") and position it at the top of the frame.
            
        2. Use a Rotate node with the Center set to the middle of the screen (0.5, 0.5) and the Angle set to 30 degrees.
            
        3. Alpha Over this rotated element on top of the original.
            
        4. Take the output of this Alpha Over and feed it back into another Rotate node (with the same settings) and Alpha Over it again.
            
        5. By chaining these nodes, you can procedurally build a perfect radial array of elements.
            
    - **Organic (Vortex / Swirl Effect):** To create a swirling distortion:
        
        1. Create a Gradient texture set to Radial. This creates an angular gradient.
            
        2. Use a Map Range node to map this gradient's output (0 to 1) to a rotation range (e.g., 0 to 360 degrees).
            
        3. Use this as the Angle input for a Rotate node. This will create a basic rotation.
            
        4. For a true vortex, you would need to use a Displace node, but driving a Rotate node with a radial gradient is a key step in building more complex rotational distortions.