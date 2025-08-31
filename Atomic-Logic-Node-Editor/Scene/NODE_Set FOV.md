- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 1 - Camera
    
- **Core Function:** Dynamically changes the Field of View (FOV) of a specified camera.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Camera / Object):** The target camera whose FOV will be changed.
        
    - **Input (FOV):** A float value representing the new field of view angle.
        
    - **Output (Done):** A flow control pulse that activates after the FOV is set.
        
- **Practical Application:** Used for visual effects like a "zoom" when aiming down sights (decreasing FOV), creating a "sprint" effect (slightly increasing FOV), or generating a disorienting warp effect by rapidly changing the FOV.