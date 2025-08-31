- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 1 - Vehicle
    
- **Core Function:** Applies a continuous braking force to the vehicle's wheels.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that applies the brake as long as it is true.
        
    - **Input (Vehicle):** The vehicle constraint to control.
        
    - **Input (Wheels):** The specific wheels to apply the brake to.
        
    - **Input (Power):** A float determining the strength of the braking force.
        
    - **Setting (Rear):** A checkbox that likely modifies which wheels are affected (e.g., applying brakes to rear wheels).
        
- **Practical Application:** Connected to the player's brake input (e.g., the 'S' key or a controller trigger). The braking force is applied every frame that the key is held down.