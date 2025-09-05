- **Editor:** Compositor Node Editor  
- **Node Group:** Keying
    
- **Core Function:** A pre-processing tool that generates a clean, idealized background plate (a "screen") for a keying node to use as a reference. It does this by analyzing the colors under tracking markers placed on an unevenly lit greenscreen, creating a smooth gradient that perfectly matches the variations in the real-world screen.
    
- **Key Properties & Settings:**
    
    - **Movie Clip (Property):** Selects the Movie Clip data-block that contains the footage and the tracking data.
        
    - **Tracking Object (Property):** Selects the specific group of tracking markers within the movie clip that are sampling the greenscreen colors.
        
    - **Gradient Detail (Property):** Controls the smoothness of the generated screen gradient.
        
    - **Samples (Property):** Sets the quality of the gradient generation.
        
- **Outputs:**
    
    - **Screen (Socket):** The primary output. This is a full-color image that represents a "perfect" version of your unevenly lit greenscreen, ready to be fed into another keying node.
        
- **Practical Application:** This node is not a keyer itself; it's a "booster rocket" for another keyer, specifically the Keying node. Its sole purpose is to solve the problem of unevenly lit backdrops, which are the number one cause of bad keys.
    
    - **Important Context (The Problem):** A real greenscreen is never a single, pure green color. It has shadows, hot spots, and wrinkles, resulting in dozens of different shades of green. A simple keyer that looks for only one Key Color will struggle to remove all of them cleanly.
        
    - **Organic (The Professional Solution for Uneven Screens):** This is the node's entire workflow.
        
        1. **Track the Screen:** In the Movie Clip Editor, place several tracking markers across the surface of the greenscreen. Place them in the bright areas, the dark areas, and the mid-tones. If the camera moves, track these markers so they stay on the screen.
            
        2. **Generate the Screen:** In the compositor, add a Keying Screen node. Select your movie clip and the tracking object containing your screen trackers. The Screen output will now be a smooth gradient that perfectly matches the color variations of your real screen.
            
        3. **Feed the Keyer:** Add a Keying node. Connect your original footage to its Image input. Crucially, connect the Screen output from the Keying Screen node directly into the Key Color input of the Keying node.
            
        4. This "organism" is now incredibly powerful. Instead of telling the Keying node to "look for this one shade of green," you are telling it to "look at this pixel in the footage, and remove it if it matches the color of the corresponding pixel in this perfect screen plate." This allows the keyer to remove a dark green color from a shadow area and a bright green color from a hot spot with equal precision, resulting in a dramatically cleaner key with far less manual tweaking.