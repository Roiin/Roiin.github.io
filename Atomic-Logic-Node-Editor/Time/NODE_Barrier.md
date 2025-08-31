- **Editor:** Logic Node Editor
    
- - **Node Group:** Time
        
- **Core Function:** Acts as a timed gate or cooldown mechanism. When triggered, it lets a signal pass through, then blocks any further signals for a specified duration.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A flow control input that attempts to pass through the barrier.
        
    - **Input (Time):** The duration in seconds that the barrier will be "closed" after a successful pass.
        
    - **Output (Out):** A flow control pulse that activates only if the barrier is "open."
        
- **Practical Application:** Used to limit the rate of player actions. For example, preventing the player from firing a weapon faster than once every 0.2 seconds, or ensuring a sound effect doesn't re-trigger too rapidly.