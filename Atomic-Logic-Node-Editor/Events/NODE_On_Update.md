- **Editor:** Logic Node Editor
- **Node Group:** Events
    
- **Core Function:** Triggers a continuous pulse of logic flow on every single logic tick (frame) that the game runs. It acts as the "heartbeat" of a logic tree for processes that need constant evaluation.
    
- **Key Properties & Settings:**
    
    - **Out (Socket):** A flow control output that activates the next node in the sequence on every frame.
        
- **Practical Application:** Essential for any action that requires constant monitoring. Examples: checking for player input (is the 'W' key pressed?), updating a character's animation state, or moving an object smoothly over time.
    
- **Glossary Connections:** Logic Tick, Game Loop