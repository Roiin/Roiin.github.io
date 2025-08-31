- **Editor:** Logic Node Editor
    
- **Node Group:** Input > Mouse
    
- **Core Function:** Rotates one or two objects (typically a player body and a camera) based on mouse movement, creating first-person or third-person camera controls.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that executes the node.
        
    - **Front (Dropdown):** Sets the object's local axis that should point forward.
        
    - **Center Mouse (Checkbox):** If checked, keeps the mouse cursor centered on the screen.
        
    - **Condition (Socket):** Boolean input to enable or disable the look functionality.
        
    - **Body (Socket):** Object input for the parent object that rotates horizontally (left/right).
        
    - **Head (Socket):** Object input for the child object that rotates vertically (up/down).
        
    - **Invert XY (Checkbox):** Inverts the direction of rotation for both axes.
        
    - **Sensitivity (Socket):** Float input that controls the speed of rotation.
        
    - **Cap Left/Right & Cap Up/Down (Checkboxes):** Enable angle limits for rotation.
        
    - **Smoothing (Socket):** Float input to smooth out the rotation movement.
        
- **Practical Application:** The cornerstone of camera control for most 3D games.