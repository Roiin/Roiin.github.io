- **Editor:** Logic Node Editor
- **Node Group:** Events
    
- **Core Function:** Monitors an input value and triggers a logic pulse whenever that value changes from one frame to the next. It is a state change detector.
    
- **Key Properties & Settings:**
    
    - **Initialize (Checkbox):** If checked, the node will also trigger on the very first frame it is evaluated, establishing a baseline.
        
    - **Value (Socket):** The data input (e.g., Float, Integer, Boolean) to be monitored.
        
    - **If Changed (Socket):** The flow control output that pulses when a change is detected.
        
    - **Old (Socket):** Outputs the value from the previous frame.
        
    - **New (Socket):** Outputs the value from the current frame.
        
- **Practical Application:** Extremely useful for triggering events based on state changes without checking every frame. Example: When a player's health property changes, this node triggers the "Update Health Bar" logic, which is far more efficient than updating the bar on every frame.