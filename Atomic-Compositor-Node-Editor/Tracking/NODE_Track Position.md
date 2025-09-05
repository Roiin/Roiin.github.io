- **Editor:** Compositor Node Editor
    
- **Node Group:** Distort
    
- **Core Function:** Extracts the raw positional (X, Y) and velocity data from a single tracking marker in the Movie Clip Editor and outputs it as numerical values. It allows you to use the motion of a point in your footage to drive any animatable parameter in the node tree.
    
- **Key Properties & Settings:**
    
    - **Movie Clip (Property):** Selects the movie clip that contains the tracking data.
        
    - **Object (Property):** Selects the tracking object that contains the specific track.
        
    - **Track (Property):** Selects the name of the individual tracking marker whose data you want to use.
        
    - **Position (Property):** Determines the coordinate system for the output (Absolute, Relative Start, etc.). Absolute is the most common, providing the marker's direct coordinates on the frame.
        
- **Outputs:**
    
    - **X (Socket):** Outputs the horizontal (X-axis) position of the tracker for the current frame.
        
    - **Y (Socket):** Outputs the vertical (Y-axis) position of the tracker for the current frame.
        
    - **Speed (Socket):** Outputs the velocity of the tracker in pixels per frame.
        
- **Practical Application:** This node is the "atom" for linking the motion of something real to something digital. It's the foundation for a huge range of motion graphics and VFX tasks.
    
    - **Molecular (Attaching an Element to a Point):** This is its most fundamental use. To make a lens flare or a text label "stick" to a moving object in your footage:
        
        1. In the Movie Clip Editor, track the point you want to attach to.
            
        2. In the compositor, add your lens flare or text element.
            
        3. Add a Transform node after your element to control its position.
            
        4. Connect the X and Y outputs of the Track Position node to the X and Y input sockets of the Transform node.
            
        5. The element will now move perfectly with the tracked point in the footage.
            
    - **Organic (Procedural Motion Blur):** The Speed output is very powerful. To add motion blur to a CG element that matches the blur of the live-action plate it's composited on:
        
        1. Track a point on a moving object in your live-action footage.
            
        2. Take the Speed output from the Track Position node.
            
        3. Use a Math node to scale this speed value appropriately.
            
        4. Feed this value into the Size input of a Blur node that is affecting your CG element.
            
        5. The CG element's blur will now increase and decrease in direct proportion to the speed of the real object, creating a much more believable integration.
            
    - **Organic (Driving Effects with Motion):** You can use the Speed output to drive almost anything. For example, you could have a sci-fi effect where a character's eyes glow brighter the faster they move.
        
        1. Track the character's eye.
            
        2. Take the Speed output and use a Map Range node to map the expected speed values (e.g., 0-10 pixels/frame) to a brightness range for a glow.
            
        3. Use this value to drive the Threshold or Size of a Glare node that is affecting only the character's eyes (isolated with a mask). The eyes will now automatically glow brighter as the character runs.