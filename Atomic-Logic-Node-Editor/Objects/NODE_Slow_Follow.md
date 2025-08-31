- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Moves an object towards a target's position with a built-in delay or smoothing, causing it to "lag behind" the target.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The object that will follow.
        
    - **Target (Socket):** The object to be followed.
        
    - **World Position (Checkbox):** Toggles between following the target's world position or local position.
        
    - **Factor (Socket):** A float (0.0 to 1.0) controlling the amount of lag. A lower value results in a slower, more delayed follow.
        
- **Practical Application:** Ideal for creating smooth "third-person" cameras that follow the player, or for pet/companion AI that trails behind the player character in a natural, less rigid manner.