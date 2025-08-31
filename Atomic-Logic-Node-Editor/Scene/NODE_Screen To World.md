- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 1 - Camera
    
- **Core Function:** Converts a 2D screen-space coordinate (like a mouse position) into a 3D point in the world space.
    
- **Key Properties & Settings:**
    
    - **Input (Camera):** The camera to use as the reference for the conversion.
        
    - **Input (Screen X, Screen Y):** The 2D pixel coordinates on the screen.
        
    - **Input (Depth):** The distance from the camera to project the point into the world.
        
    - **Output (World Position):** The resulting 3D vector coordinate in the game world.
        
- **Practical Application:** The foundation for mouse-based interaction in a 3D world. Used for clicking on objects to select them, determining where to move a character in a point-and-click game, or aiming where a projectile should be fired based on the cursor's position.