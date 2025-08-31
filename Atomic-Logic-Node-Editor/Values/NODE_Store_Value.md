- **Editor:** Logic Node Editor
    
- **Node Group:** Values
    
- **Core Function:** Acts as a variable container within a logic tree. It stores an incoming value when initialized and outputs that stored value whenever requested.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Initialize (Socket):** A boolean input. When True, the node captures and stores the current Value input.
        
    - **Condition (Socket):** A boolean input that must be True for initialization to occur.
        
    - **Value (Socket):** The data input to be stored.
        
    - **Stored Value (Socket):** The data output, providing the value that is currently stored in the node.
        
- **Practical Application:** Useful for "caching" a value at a specific moment. For example, storing a character's position when they step on a pressure plate, so they can be teleported back to that exact stored position later.