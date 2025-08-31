- **Editor:** Logic Node Editor
    
- **Node Group:** Values
    
- **Core Function:** A data-based switch. It outputs one of two provided values based on the state of a boolean Condition.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** The boolean input that controls the switch.
        
    - **A if True, else B (Socket):** The data output.
        
    - **A (Socket):** The value to output if the Condition is True.
        
    - **B (Socket):** The value to output if the Condition is False.
        
- **Practical Application:** Used to select between two data paths. For example, if a player is sprinting (IsSprinting is True), this node can be used to select a move_speed of 10.0 (value A); otherwise, it selects 5.0 (value B).