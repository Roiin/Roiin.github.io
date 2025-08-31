- **Editor:** Logic Node Editor
    
- **Node Group:** Utility
    
- **Core Function:** Prints the value of its input to the system console window. This is the most fundamental debugging tool.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the print to occur.
        
    - **Input (Value):** The data (float, string, object, etc.) to be printed to the console.
        
    - **Output (Done):** A flow control pulse that activates after the print action is complete.
        
- **Practical Application:** The go-to node for debugging any problem. You can connect the output of any node to the Value input to see exactly what data is flowing through your logic at any given moment. For example, printing the player's health every time they take damage to verify the calculation is correct.