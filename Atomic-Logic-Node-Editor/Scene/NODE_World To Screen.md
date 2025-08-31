- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 1 - Camera
    
- **Core Function:** Converts a 3D world-space coordinate into a 2D screen-space coordinate (pixel position).
    
- **Key Properties & Settings:**
    
    - **Input (Camera):** The camera to use as the reference for the conversion.
        
    - **Input (Point):** The 3D vector (X, Y, Z) of the point in the game world.
        
    - **Output (On Screen):** A Boolean that is true if the 3D point is currently visible on the camera's screen.
        
    - **Output (X, Y, Z):** The resulting 2D coordinates (and depth information) on the screen.
        
- **Practical Application:** Essential for user interfaces (UI). Used to place a health bar above an enemy's head, display an objective marker over a location in the distance, or show a name tag on another player.