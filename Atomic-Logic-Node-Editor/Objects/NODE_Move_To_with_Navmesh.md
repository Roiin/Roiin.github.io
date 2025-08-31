- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Moves an object towards a target destination, using a navigation mesh (Navmesh) to calculate the path and avoid obstacles. This is a core node for AI pathfinding.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that starts or continues the movement.
        
    - **Condition (Socket):** A boolean input.
        
    - **Moving Object (Socket):** The object to move (must be a physics Actor).
        
    - **Rotating Object (Socket):** The object to rotate to face the direction of movement.
        
    - **Navmesh Object (Socket):** An object input for the Navmesh data.
        
    - **Destination (Socket):** A 3D vector input for the target world coordinates.
        
    - **Move as Dynamic (Checkbox):** Toggles between physics-based or kinematic movement.
        
    - **Lin Speed (Socket):** A float controlling the linear speed.
        
    - **Reach Threshold (Socket):** A float defining the distance from the destination to stop.
        
    - **Look At (Checkbox):** Toggles automatic rotation towards the path.
        
- **Practical Application:** The primary tool for enabling NPCs and enemies to navigate complex levels. An enemy AI would get the player's world position, feed it into the Destination socket, and this node would handle moving the enemy around walls and obstacles to reach the player.