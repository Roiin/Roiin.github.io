- **Editor:** Logic Node Editor
    
- **Node Group:** Animation
    
- **Core Function:** Plays an animation Action on a specified Object or Armature. This is the primary node for triggering any character or object animation.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** A boolean input; the animation will only start or continue playing on frames where this is True.
        
    - **Object/Armature (Socket):** The target object or armature that contains the animation Action.
        
    - **Action (Socket):** A string input for the name of the Action to play (e.g., "WalkCycle", "Attack_01").
        
    - **Start (Socket):** A float input defining the frame on which the animation should start.
        
    - **End (Socket):** A float input defining the frame on which the animation should end.
        
    - **Layer (Socket):** An integer input (0-15) specifying the animation layer. Higher layers override lower ones, allowing for animation blending.
        
    - **Play (Dropdown):** Determines the playback mode (e.g., Loop, Play, Ping Pong).
        
    - **Intensity (Socket):** A float input (0.0 to 1.0) controlling the influence of this animation on its layer, used for blending.
        
    - **Speed (Socket):** A float input controlling the playback speed of the animation (1.0 is normal speed).
        
    - **Blend-In (Socket):** A float input defining the number of frames over which to smoothly blend this animation in.
        
    - **Blend... (Socket):** Likely Blend-Out. A float input defining the number of frames over which to smoothly blend this animation out.
        
    - **Started (Socket):** Flow output that pulses once on the frame the animation begins playing.
        
    - **Running (Socket):** Flow output that pulses continuously on every frame the animation is actively playing.
        
    - **On Finish (Socket):** Flow output that pulses once on the frame the animation completes.
        
    - **Current Frame (Socket):** A float output providing the current playback frame of the animation.
        
- **Practical Application:** The core of any animation system. A Keyboard Key (W) node's output is connected to the Condition socket to play a "WalkCycle" animation. An On Finish pulse can be used to chain animations together, like transitioning from an "Attack" animation to an "Idle" animation.