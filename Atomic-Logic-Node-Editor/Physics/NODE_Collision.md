- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 3
    
- **Core Function:** An event node that triggers its logic flow when the host object collides with another physics object that matches specified criteria.
    
- **Key Properties & Settings:**
    
    - **Input (Property / Material):** Optional string inputs to filter collisions, only triggering if the other object has a specific property or material.
        
    - **Setting (Continuous):** If checked, the On Collision output pulses every frame the collision persists. If unchecked, it pulses only on the first frame of impact.
        
    - **Output (On Collision):** A flow control pulse that activates when a valid collision occurs.
        
    - **Output (Colliding Object):** The other object involved in the collision.
        
    - **Output (Point):** The world-space vector position of the collision impact point.
        
    - **Output (Normal):** The surface normal vector at the point of impact.
        
- **Practical Application:** The foundation of all physical interactions. Used to detect a bullet hitting a target, the player touching a trigger, or a vehicle crashing into a wall.