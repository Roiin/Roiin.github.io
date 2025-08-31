- **Editor:** Logic Node Editor
    
- **Node Group:** Utility
    
- **Core Function:** Draws a debug line in the 3D viewport between two specified points. The line is only visible in-game and is meant for debugging purposes.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the line to be drawn.
        
    - **Input (Color):** Sets the color of the debug line.
        
    - **Input (Origin):** A vector for the starting point of the line.
        
    - **Input (Target):** A vector for the ending point of the line.
        
    - **Output (Done):** A flow control pulse that activates after the draw command is issued for the frame.
        
- **Practical Application:** A visual debugging tool. It's used to visualize raycasts, AI line-of-sight, patrol paths, or the direction a character is facing. It helps you "see" the invisible logic of your game in the 3D space.