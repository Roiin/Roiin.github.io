- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 4
    
- **Core Function:** Sets the speed of the game's overall simulation.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Timescale):** A float value for the new speed. 1.0 is normal, 0.5 is half-speed (slow-motion), and 0.0 effectively pauses the simulation.
        
    - **Output (Done):** A flow control pulse that activates after the timescale is set.
        
- **Practical Application:** Essential for creating "bullet-time" or slow-motion effects during dramatic moments. It can also be used to pause the game logic while still allowing menus or camera movements to function.