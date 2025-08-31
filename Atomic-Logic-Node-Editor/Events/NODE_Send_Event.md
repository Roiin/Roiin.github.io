- **Editor:** Logic Node Editor
- **Node Group:** Events
    
- **Core Function:** Broadcasts a named event, optionally with attached data ("Content"), to a specified target or globally. It is the "transmitter" in an event-driven system.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the sending of the event.
        
    - **Use Content (Checkbox):** Enables the Content input socket.
        
    - **Use Target (Checkbox):** Enables the Target input socket. If unchecked, the event is broadcast globally.
        
    - **Condition (Socket):** A Boolean input. The event will only be sent if this condition is True.
        
    - **Content (Socket):** The data (e.g., a number, string, or object reference) to be sent with the event.
        
    - **Subject (Socket):** A string input that defines the name of the event (e.g., "PlayerTookDamage").
        
    - **Target (Socket):** An object input that specifies which object should receive the event.
        
- **Practical Application:** Decouples logic between objects. A pressure plate sends the event "DoorOpen" to a specific Target door. A power-up sends a global "PlayerPoweredUp" event.