- **Editor:** Logic Node Editor
    
- **Node Group:** Raycasts
    
- **Core Function:** Casts a ray originating from the camera's position, directed towards a specific point on the screen (typically the center).
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the raycast to be performed.
        
    - **Input (Aim):** A 2D vector (0.5, 0.5 represents the exact center of the screen) that defines the ray's direction.
        
    - **Input (Distance):** A float that sets the maximum length of the ray.
        
    - **Input (Power, Resolution):** Floats that likely control advanced properties, possibly for a sphere-cast (a "fat" ray) or for applying a physics force on impact.
        
    - **Input (Property):** An optional string to filter for a specific object property.
        
    - **Setting (Visualize):** If checked, draws a debug line for the ray.
        
    - **Output (Has Result, Picked Object, etc.):** Provides the standard collision information.
        
- **Practical Application:** The standard method for implementing aiming and interaction in first-person or third-person "over-the-shoulder" games. It's used to determine what the player is looking at in the center of their screen, for shooting, picking up items, or displaying interaction prompts like "Press 'F' to open".