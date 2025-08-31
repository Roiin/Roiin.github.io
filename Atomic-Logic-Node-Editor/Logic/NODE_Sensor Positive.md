- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 2 - Bricks
    
- **Core Function:** Provides a continuous output indicating if a specific legacy Logic Brick Sensor is currently positive (i.e., its conditions are met), acting as a direct bridge from sensor events to node logic.
    
- **Key Properties & Settings:**
    
    - **Input (Object):** The object that owns the sensor.
        
    - **Input (Sensor):** The name of the Sensor to check.
        
    - **Output (Positive):** A boolean that is true as long as the sensor's conditions are met.
        
- **Practical Application:** The most direct way to integrate Logic Bricks. For example, using the Positive output from a Keyboard sensor to trigger a complex jump sequence managed entirely by nodes.