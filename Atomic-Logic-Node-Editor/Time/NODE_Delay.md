- **Editor:** Logic Node Editor
    
- **Node Group:** Time
    
- **Core Function:** Acts as a simple timer. When its Condition input receives a true signal, it waits for a specified duration before sending a single pulse through its Out socket.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that triggers the delay when it becomes true.
        
    - **Input (Delay):** A float for the duration of the delay in seconds.
        
    - **Output (Out):** A flow control pulse that activates after the delay has finished.
        
- **Practical Application:** Creating timed sequences. For example, after a player presses a button, there is a 2-second Delay before a door opens.