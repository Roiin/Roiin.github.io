- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 1 - Vehicle
    
- **Core Function:** Applies a continuous engine force to the vehicle's drive wheels, causing it to accelerate.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that applies engine force as long as it is true.
        
    - **Input (Vehicle):** The vehicle constraint to control.
        
    - **Input (Wheels):** The specific wheels that will receive engine power (the drive wheels).
        
    - **Input (Power):** A float determining the strength of the engine force.
        
    - **Setting (Rear):** A checkbox, likely to specify a rear-wheel-drive configuration.
        
- **Practical Application:** Connected to the player's throttle input (e.g., the 'W' key). The vehicle accelerates as long as the input is active.