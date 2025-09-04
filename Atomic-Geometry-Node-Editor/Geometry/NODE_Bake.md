- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Caches the output of a complex and computationally expensive part of a node tree to disk or into the .blend file. This allows for real-time playback and faster processing of downstream nodes by replacing heavy, on-the-fly calculations with a simple, pre-computed data lookup.
    
- **Key Properties & Settings:**
    
    - **Geometry & Bake Items (Sockets):** The primary input is Geometry, but multiple data streams (like attributes) can be added and baked simultaneously. The node acts as a passthrough, outputting the baked data from corresponding output sockets.
        
    - **Bake Mode (Property):**
        
        - **Still:** Bakes the geometry for the single, current frame.
            
        - **Animation:** Bakes the geometry for a range of frames.
            
    - **Primary Controls (Buttons):**
        
        - **Bake:** Starts the calculation and saving process. This can take time.
            
        - **Delete:** Clears the baked cache.
            
        - **Pack/Unpack:** Manages whether the baked data is stored inside the .blend file or as external files.
            
    - **Storage Options (Properties):** Controls where the baked data is saved (e.g., 'Packed' inside the file, or 'Disk' in an external folder).
        
- **Practical Application:** This node is absolutely essential when working with simulations. Imagine you've created a complex particle simulation of an animal statue crumbling into dust using a Simulation Zone.
    
    - **The Problem:** Every time you want to view the animation, Blender has to re-calculate the entire simulation from frame 1. This makes it impossible to scrub the timeline or play the animation in real-time.
        
    - **The Solution:**
        
        1. Place a Bake node immediately after the Simulation Zone's output.
            
        2. Set the Bake Mode to 'Animation' and ensure the frame range covers your entire effect.
            
        3. Click the Bake button. You'll wait while Blender processes the simulation once and saves the state of every particle on every frame to a cache file.
            
        4. **The Result:** Once the bake is complete, the Bake node no longer runs the heavy simulation. It simply reads the saved file for the current frame. Now you can scrub the timeline back and forth instantly, play the animation in real-time to check the timing, and render frames in any order you wish. The performance is massively improved because the hard work has already been done and saved.