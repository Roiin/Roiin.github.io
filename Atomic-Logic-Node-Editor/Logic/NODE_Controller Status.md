- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 2 - Bricks
    
- **Core Function:** Checks the status of a legacy Logic Brick Controller, allowing nodes to determine if a brick-based logic state is active.
    
- **Key Properties & Settings:**
    
    - **Input (Object):** The object that owns the controller.
        
    - **Input (Controller):** The name of the Controller to check.
        
    - **Output (Status):** A boolean that is true if the controller is active.
        
    - **Output (Sensors):** A list of the sensors connected to the controller.
        
- **Practical Application:** A way to check from the node system if a complex logic brick setup (e.g., a state machine) is currently active, without needing to replicate all its sensor conditions in nodes.