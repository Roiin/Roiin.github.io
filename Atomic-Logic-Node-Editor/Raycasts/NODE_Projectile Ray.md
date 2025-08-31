- **Editor:** Logic Node Editor
    
- **Node Group:** Raycasts
    
- **Core Function:** Simulates and casts a ray along a parabolic (arced) trajectory, mimicking the path of a projectile under the influence of gravity.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the raycast to be performed.
        
    - **Input (Origin):** A vector for the starting point of the projectile.
        
    - **Input (Aim):** A vector likely representing the initial velocity or force applied to the projectile, which defines the arc's shape.
        
    - **Output (Has Result, Picked Object, etc.):** Provides collision information along the predicted arc.
        
- **Practical Application:** Essential for aiming systems that involve lobbed projectiles like grenades, arrows, or mortar shells. It allows the game to draw a "prediction arc" to show the player where their shot will land.