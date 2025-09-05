- **Editor:** Compositor Node Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Provides the current animation time as a numerical value, allowing for the creation of time-based and procedural animations directly within the node tree without manual keyframing.
    
- **Key Properties & Settings:**
    
    - This node has no properties.
        
- **Outputs:**
    
    - **Seconds (Socket):** Outputs the current scene time in seconds (e.g., at frame 48 in a 24fps scene, this would output 2.0).
        
    - **Frames (Socket):** Outputs the current scene frame number (e.g., 48). This value can be a float (non-integer) to support sub-frame calculations for high-quality motion blur.
        
- **Practical Application:** This node is the engine for any effect that needs to change or evolve over time automatically.
    
    - **Molecular (Evolving Procedural Textures):** To create an animated effect like boiling clouds, magical energy, or rippling water.
        
        1. Create a Texture node (e.g., with a Clouds texture).
            
        2. Connect the Frames output from the Scene Time node to a Combine XYZ node, plugging it into the Z input.
            
        3. Feed the vector output of Combine XYZ into the Offset socket of the Texture node.
            
        4. Now, as the animation plays, the texture will evolve and change on every frame, creating a dynamic, looping animation with zero keyframes.
            
    - **Molecular (Procedural Flicker/Glitch):** To simulate a flickering light or a digital glitch.
        
        1. Take the Frames output and feed it into a Math node set to Sine. This creates a smooth oscillation.
            
        2. For a more random flicker, multiply this result with the output of a procedural Noise texture.
            
        3. Use this rapidly changing value to drive the Factor of a Mix node (to flash a bright color) or the Threshold of a Glare node. The result is an automatic, chaotic flicker effect.
            
    - **Organic (Procedural Countdown Timer):** This demonstrates building a motion graphics "organism." Imagine you need a 10-second countdown at 24fps.
        
        1. Use a Math node with the formula: (241 - Frames) / 24. At frame 1, this outputs 10. At frame 25, it outputs 9, and so on.
            
        2. Feed this numerical result into a Value to String node to convert it to text.
            
        3. Use the output of Value to String to drive the input of a Text node.
            
        4. Composite this Text node over your footage. You have now created a fully procedural countdown timer that is perfectly synced to the timeline without ever setting a single keyframe on the text itself.