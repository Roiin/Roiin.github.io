- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 1 - Camera
    
- **Core Function:** Adjusts the scale (zoom level) of a camera that is in orthographic (non-perspective) mode.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Camera / Object):** The target orthographic camera.
        
    - **Input (Scale):** A float value for the new orthographic scale.
        
    - **Output (Done):** A flow control pulse that activates after the scale is set.
        
- **Practical Application:** The primary way to zoom in and out in a 2D or top-down game that uses an orthographic camera, for example, zooming out to show more of a strategy map.