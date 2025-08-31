- **Editor:** Logic Node Editor
    
- **Node Group:** Animation
    
- **Core Function:** Manually sets the current frame of an animation Action on a specified Object or Armature. This does not play the animation, but rather jumps it to a specific point in time.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Object (Socket):** The target object or armature.
        
    - **Action (Socket):** A string input for the name of the Action to modify.
        
    - **Layer (Socket):** An integer input for the animation layer.
        
    - **Frame (Socket):** A float input for the specific frame number to set the animation to.
        
    - **Freeze (Checkbox):** If checked, holds the animation at the specified frame.
        
    - **Layer Weight (Socket):** A float input (0.0 to 1.0) to control the influence of this pose on the specified layer.
        
- **Practical Application:** Useful for procedural animation or specific poses. You could link a character's "lean" animation frame to the mouse's X-axis movement, allowing the player to control the degree of the lean in real-time by scrubbing through the animation.