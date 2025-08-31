- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Moves an object smoothly towards a target location over a period of time, without requiring physics.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that starts or continues the movement.
        
    - **Condition (Socket):** A boolean input; movement only occurs when this is True.
        
    - **Object (Socket):** The object to be moved.
        
    - **Target Location (Socket):** A 3D vector for the destination coordinates.
        
    - **Move as Dynamic (Checkbox):** If checked, attempts to use physics to move the object.
        
    - **Speed (Socket):** A float controlling the speed of the movement.
        
    - **Stop At Distance (Socket):** A float defining the distance from the target at which the object should stop.
        
    - **Reached (Socket):** A flow control output that pulses once when the object reaches the target location.
        
- **Practical Application:** Ideal for non-player character (NPC) pathing, moving platforms, or cinematic object movements. An NPC can be told to move to a waypoint, and the Reached output can trigger the logic to move to the next waypoint in a sequence.