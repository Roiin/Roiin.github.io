- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** Warps an image by shifting its pixels according to the color values of a second input image (a "displacement map"). It is the core tool for creating procedural distortions like heat haze, water ripples, and refractions.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input that you want to distort.
        
    - **Vector (Socket):** The crucial control input. This is the displacement map.
        
        - The **Red** channel of this input controls the horizontal (X-axis) displacement.
            
        - The **Green** channel of this input controls the vertical (Y-axis) displacement.
            
        - By default, a mid-gray (0.5, 0.5, 0.5) value results in no displacement.
            
    - **Scale (Socket):** A multiplier that controls the overall strength of the displacement effect.
        
- **Practical Application:** The Displace node is an "atom" whose power is entirely defined by the displacement map you feed into it. Its applications are nearly limitless.
    
    - **Molecular (Heat Haze / Mirage):** This is a classic VFX "molecule."
        
        1. Create an animated, low-frequency Noise Texture (often called a "boiling" noise by animating the W value in 4D mode).
            
        2. Connect this Noise Texture to the Vector input of a Displace node.
            
        3. Connect your main footage to the Image input.
            
        4. Adjust the Scale to a small value. The result is a shimmering, wavy distortion that perfectly simulates heat haze from a jet engine, a desert floor, or a fire.
            
    - **Molecular (Water Ripples / Underwater Distortion):** The same principle as heat haze, but with different noise settings. A Wave Texture set to Rings can also be used as the displacement map to create concentric ripples.
        
    - **Organic (Fake Glass Refraction):** To make a 2D image look like it's behind a pane of bumpy, imperfect glass:
        
        1. Take the Normal pass of your glass object from the Render Layers. The Normal pass's red and green channels contain exactly the kind of directional information the Displace node needs.
            
        2. Feed your background image into the Image socket of a Displace node.
            
        3. Feed the Normal pass into the Vector socket.
            
        4. You may need to use a Separate/Combine RGBA and Math nodes to re-center the Normal pass data (which ranges from -1 to 1) into the 0 to 1 range the Displace node expects.
            
        5. The result is a background that is distorted in a way that perfectly matches the contours of the glass, creating a very convincing refraction effect.
            
    - **Organic (Glitch and Data Moshing):** The Displace node is the heart of most procedural glitch effects.
        
        1. Create a Brick Texture or Checker Texture to divide the screen into blocks.
            
        2. Use a White Noise texture seeded by the cell positions of that brick texture to generate a random R/G vector for each block.
            
        3. Feed this random vector map into the Displace node.
            
        4. The result is a "data moshing" effect where entire blocks of the image are randomly shifted, creating a classic digital corruption look.