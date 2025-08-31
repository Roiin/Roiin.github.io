- **Editor:** Logic Node Editor
    
- **Node Group:** Values
    
- **Core Function:** Selects a value from a list of inputs based on an integer Switch value. Acts like a 'case' or 'select' statement for data.
    
- **Key Properties & Settings:**
    
    - **Switch (Socket):** An integer input. If the value is 0, it outputs Case A; if 1, it outputs Case B, and so on.
        
    - **Result (Socket):** The selected data output.
        
    - **Default (Socket):** The value to output if the Switch integer does not correspond to any available Case.
        
    - **Case A, Case B, ... (Sockets):** The list of possible data values to choose from.
        
- **Practical Application:** Useful for selecting an outcome from multiple possibilities. For example, selecting a weapon damage value based on the currently equipped weapon's ID number, or choosing a dialogue line from a list.