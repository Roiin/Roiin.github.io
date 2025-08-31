- **Editor:** Logic Node Editor
- **Node Group:** Events
    
- **Core Function:** Listens for a specific named event. When the event is received, it triggers a logic flow and provides access to any data that was sent with it. It is the "receiver" in an event-driven system.
    
- **Key Properties & Settings:**
    
    - **Use Target (Checkbox):** If checked, the node will only listen for events sent specifically to the object containing this logic tree.
        
    - **Subject (Socket):** A string input that specifies the name of the event to listen for.
        
    - **Received (Socket):** The flow control output that pulses when the event is received.
        
    - **Content (Socket):** Outputs the data that was sent with the event.
        
    - **Messenger (Socket):** Outputs a reference to the object that sent the event.
        
- **Practical Application:** A door with this node listens for the "DoorOpen" Subject. When it receives the event, it plays its opening animation.