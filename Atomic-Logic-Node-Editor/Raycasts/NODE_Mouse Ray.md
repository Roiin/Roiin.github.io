- **Editor:** Logic Node Editor
    
- **Node Group:** Raycasts
    
- **Core Function:** Casts a ray from the camera's position, through the current position of the mouse cursor, and into the 3D scene.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the raycast to be performed.
        
    - **Input (Distance):** A float that sets the maximum length of the ray.
        
    - **Input (Property):** An optional string to filter for a specific object property.
        
    - **Setting (X-Ray):** If checked, allows the ray to hit objects behind others.
        
    - **Output (Has Result, Picked Object, etc.):** Provides the standard collision information.
        
- **Practical Application:** The cornerstone of any mouse-driven 3D interaction. Used for selecting units in a strategy game, clicking on objects to interact with them, or aiming/firing a weapon directly where the player is pointing their cursor.