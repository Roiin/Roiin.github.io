- **Editor:** Logic Node Editor
- **Node Group:** Events
    
- **Core Function:** Acts as a gate that allows the logic flow to pass through it only a single time. After the first pulse, it closes and will not activate again unless the Repeat input receives a True signal.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** The initial flow control input.
        
    - **Repeat (Socket):** A boolean input. If it receives a True signal, the node resets and can be triggered again.
        
    - **Out (Socket):** The flow control output that pulses only once.
        
- **Practical Application:** Perfect for one-time events like unlocking a door, playing a specific discovery sound effect, or triggering an introductory tutorial message.