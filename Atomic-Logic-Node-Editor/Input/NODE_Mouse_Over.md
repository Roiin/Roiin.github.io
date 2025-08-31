- **Editor:** Logic Node Editor
    
- **Node Group:** Input > Mouse
    
- **Core Function:** Detects when the mouse cursor is hovering over an object with collision enabled.
    
- **Key Properties & Settings:**
    
    - **On Enter (Socket):** Flow output that pulses once when the cursor first enters the object's collision bounds.
        
    - **On Over (Socket):** Flow output that pulses continuously on every frame the cursor is over the object.
        
    - **On Exit (Socket):** Flow output that pulses once when the cursor leaves the object's collision bounds.
        
    - **Point (Socket):** Vector output providing the world coordinate of the hit point.
        
    - **Normal (Socket):** Vector output providing the surface normal at the hit point.
        
    - **Object (Socket):** Object output providing a reference to the object being hovered over.
        
- **Practical Application:** Used for highlighting interactive objects, displaying tooltips, or creating hover-sensitive UI buttons.