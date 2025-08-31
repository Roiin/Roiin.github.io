- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 1 - Vehicle
    
- **Core Function:** Applies a continuous steering angle to the vehicle's wheels.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that enables steering as long as it is true.
        
    - **Input (Vehicle):** The vehicle constraint to control.
        
    - **Input (Wheels):** The specific wheels that will be used for steering.
        
    - **Input (Steer):** A float value representing the steering angle. Negative values typically steer left, positive values steer right.
        
    - **Setting (Rear):** A checkbox, likely for enabling rear-wheel steering.
        
- **Practical Application:** The Steer input is typically connected to an analog axis (joystick or keyboard 'A'/'D' keys mapped to values like -1.0 and 1.0) to allow for variable steering control.