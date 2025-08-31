- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 2 - Character
    
- **Core Function:** Applies a continuous directional movement force to an object with "Character" physics type. This is the primary node for player movement.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that enables movement as long as it is true.
        
    - **Input (Object):** The character object to be moved.
        
    - **Input (Vector):** A 3D vector representing the desired direction and speed of movement.
        
    - **Setting (Local):** If checked, the movement vector is interpreted relative to the character's own orientation (e.g., a positive Y vector always means "forward"). If unchecked, it's interpreted in world space (e.g., positive Y is always world "North").
        
    - **Output (Done):** A flow control pulse that activates each frame the movement is applied.
        
- **Practical Application:** The core of a character controller. The Vector input is typically fed by player inputs (WASD keys or joystick) to control the character's walking and strafing.