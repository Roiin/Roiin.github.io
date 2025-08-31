- **Editor:** Logic Node Editor
    
- **Node Group:** Input > Gamepad
    
- **Core Function:** Rotates objects based on the input from a gamepad's analog stick, typically the right stick.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** Flow control input.
        
    - **Right Stick (Checkbox):** Toggles the use of the right stick for input.
        
    - **Condition (Socket):** Boolean to enable/disable the node's function.
        
    - **Body/Head (Sockets):** Object inputs for horizontal and vertical rotation targets.
        
    - **Invert XY, Index, Sensitivity, Exponent, Cap Left/Right, Cap Up/Down, Threshold:** Sockets and checkboxes to fine-tune the look controls.
        
- **Practical Application:** The standard method for implementing camera controls for a gamepad in a 3D game.