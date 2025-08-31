- **Editor:** Logic Node Editor
    
- **Node Group:** Raycasts
    
- **Core Function:** The most fundamental raycast node. It casts a single, straight-line ray from a specified origin point to a specified target point and reports if it collides with any physics objects along its path.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the raycast to be performed.
        
    - **Input (Origin):** A vector defining the starting point of the ray.
        
    - **Input (Target):** A vector defining the ending point of the ray.
        
    - **Input (Property/Material):** Optional string filters to only detect hits on objects with a specific property or material.
        
    - **Input (Exclude):** An object to be explicitly ignored by this raycast.
        
    - **Setting (X-Ray):** If checked, the ray will detect objects even if they are behind other surfaces.
        
    - **Setting (Visualize):** If checked, a debug line is drawn in the viewport representing the ray.
        
    - **Output (Has Result):** A Boolean that is true if the ray hit an object.
        
    - **Output (Picked Object, Picked Point, Picked Normal):** The object, world position, and surface normal of the impact point, respectively.
        
- **Practical Application:** A universal tool for detection. Used for AI line-of-sight checks ("Can I see the player?"), determining if the ground is beneath a character before allowing a jump, or creating laser tripwires.