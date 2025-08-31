- **Editor:** Logic Node Editor
    
- **Node Group:** Render
    
- **Core Function:** Toggles the visibility of the advanced engine profiler, which displays detailed performance metrics.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Show):** A boolean; true to display the profiler, false to hide it.
        
    - **Output (Done):** A flow control pulse that activates after the visibility is changed.
        
- **Practical Application:** An advanced debug tool used by developers to diagnose performance issues by seeing a detailed breakdown of engine processes (e.g., time spent on Physics, Logic, Rasterizer).