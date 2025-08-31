- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 6
    
- **Core Function:** Spawns a new object into the scene at a specified location and orientation.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object to Add):** The object from which the new instance will be created (e.g., a bullet object).
        
    - **Input (Object):** An optional object whose position/rotation will be copied for the spawn location.
        
    - **Input (Life):** A float value determining how many seconds the spawned object will exist before being automatically removed. A value of 0 means it lasts forever.
        
    - **Setting (Full Copy):** If checked, creates a full copy of the object including its logic trees and physics, which can be performance-intensive.
        
    - **Output (Added Object):** The newly created object instance.
        
    - **Output (Done):** A flow control pulse that activates after the object is added.
        
- **Practical Application:** The primary node for spawning anything in-game: bullets from a gun, enemies from a spawner, or debris from an explosion.