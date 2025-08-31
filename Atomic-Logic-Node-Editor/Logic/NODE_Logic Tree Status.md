- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 1 - Trees
    
- **Core Function:** A conditional node that checks the current execution state of a Logic Tree on an object and provides continuous output based on that state.
    
- **Key Properties & Settings:**
    
    - **Input (Object):** The object to check.
        
    - **Input (Node Tree):** The specific Logic Tree whose status is being queried.
        
    - **Output (Running):** A continuous flow control output that is active every frame the tree is running.
        
    - **Output (Stopped):** A continuous flow control output that is active every frame the tree is not running.
        
- **Practical Application:** Used to create state-dependent logic. For example, a door might only open if an NPC's "GuardDuty" logic tree is in the Stopped state.