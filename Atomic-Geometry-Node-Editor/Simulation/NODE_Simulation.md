- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Simulation
    
- **Core Function:** Creates a "Simulation Zone" where the output of the previous animation frame is fed back as the input for the current frame. This allows for the creation of stateful, time-dependent effects like physics simulations, growth systems, and accumulating processes where each frame builds upon the last. **Note: This node structure can only be used in the modifier context, not for custom tools.**
    
- **Structure:**
    
    - **Simulation Input Node:** The entry point to the zone. Geometry and data connected here are the initial state of the simulation at frame 1. It also has a Delta Time output (time since last frame) which is crucial for frame-rate independent physics.
        
    - **Simulation Output Node:** The exit point. The geometry connected here at the end of a frame becomes the input geometry for the next frame. It also serves as the final output of the entire modifier for rendering.
        
- **Key Properties & Settings:**
    
    - **Adding State:** You can add new sockets to the Simulation Input and Output nodes by dragging a connection from any node inside the zone to their blank sockets. This allows you to "remember" any kind of data (not just geometry) between frames, such as velocity vectors, age attributes, or scores.
        
    - **Delta Time (Socket - Output on Input Node):** The time in seconds that has passed since the last frame. Multiplying velocity by Delta Time ensures that simulations run at the same speed regardless of the scene's frame rate.
        
    - **Baking:** Simulations are automatically cached to memory during playback. For final renders or complex simulations, they can be baked to disk from the Physics Properties panel, which saves the state of every frame to a file.
        
- **Practical Application:** The Simulation Zone is perfect for creating dynamic physics-based animations, like a colony of simple, particle-based "creatures" that are attracted to a target.
    
    1. **The Setup (Initial State):** Before the Simulation Input, create a point cloud of your "creatures" with a Distribute Points on Faces node. Store a starting velocity attribute of (0,0,0) on these points.
        
    2. **Inside the Zone (The Rules for One Frame):**
        
        - The Simulation Input provides the position and velocity of the creatures from the previous frame.
            
        - **Calculate Force:** Find the direction vector from each creature's position to a target (like an animated Empty). This is your acceleration vector.
            
        - **Update Velocity:** Add this acceleration vector (multiplied by Delta Time) to the previous frame's velocity. This is your new velocity.
            
        - **Update Position:** Add this new velocity (also multiplied by Delta Time) to the creature's current position. Use a Set Position node to move the points.
            
    3. **The Output:**
        
        - Connect the final, moved geometry to the Simulation Output's geometry socket.
            
        - Connect the new, updated velocity attribute to a new socket on the Simulation Output. This is crucial, as it "saves" the velocity for the next frame.
            
    4. **The Result:** When you press play, the simulation loop begins. Each frame, the creatures look at the target, adjust their velocity, and move a little bit. Because their velocity is remembered, they build up momentum and will realistically swarm and orbit the target. This complex, life-like motion emerges from the simple set of rules that are applied iteratively inside the Simulation Zone.