- **Editor:** Logic Node Editor
    
- **Node Group:** Time
    
- **Core Function:** A passive node that provides the time passed since the last frame was rendered. This is the single most important node for frame-rate independence.
    
- **Key Properties & Settings:**
    
    - **Output (Delta (Frametime)):** A float representing the time in seconds since the previous frame.
        
- **Practical Application:** Essential for smooth, consistent motion and logic regardless of performance. Any continuous operation, like moving an object, should be multiplied by this delta value. Movement = Speed * Delta.