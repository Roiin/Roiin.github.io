- **Editor:** Logic Node Editor
    
- **Node Group:** Input > Mouse
    
- **Core Function:** Triggers a logic flow when the mouse cursor moves. This is purely an event trigger and does not output position data itself.
    
- **Key Properties & Settings:**
    
    - **Each Frame (Checkbox):** If checked, pulses every frame that movement occurs. If unchecked, it pulses only once when movement begins and then waits for the mouse to stop before it can trigger again.
        
    - **If Moved (Socket):** A flow control output that pulses when movement is detected.
        
- **Practical Application:** Can be used to wake a game from an "attract mode" or to trigger UI changes when the player starts interacting with the mouse.