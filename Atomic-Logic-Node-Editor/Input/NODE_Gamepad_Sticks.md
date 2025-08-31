- **Editor:** Logic Node Editor
    
- **Node Group:** Input > Gamepad
    
- **Core Function:** Outputs the vector data from a gamepad's analog sticks.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** Vector output providing the X and Y values of the selected stick.
        
    - **Stick (Dropdown):** Selects which stick to read from (Left Stick or Right Stick).
        
    - **Invert XY, Index, Sensitivity, Threshold:** Sockets and checkboxes for fine-tuning stick input.
        
- **Practical Application:** The standard method for character movement. The Vector output is typically fed into an Apply Movement node.