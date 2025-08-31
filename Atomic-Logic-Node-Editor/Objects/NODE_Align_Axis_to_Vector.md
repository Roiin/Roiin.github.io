- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Rotates an object so that one of its local axes points towards a specified world-space vector (direction).
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A Boolean input.
        
    - **Object (Socket):** The object to rotate.
        
    - **Vector (Socket):** The 3D direction vector to align with.
        
    - **Axis (Dropdown):** The local axis of the object that will be aligned (e.g., +X, -Y).
        
    - **Factor (Socket):** A float (0.0 to 1.0) controlling the speed of the alignment, allowing for smooth turning. A factor of 1.0 results in an instant snap.
        
- **Practical Application:** Used for making objects "look at" a direction. For example, making a security camera's +Y axis always point towards the player's position (by subtracting the camera's position from the player's position to get the direction vector).