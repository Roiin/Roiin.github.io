- **Editor:** Logic Node Editor
    
- **Node Group:** Network
    
- **Core Function:** Establishes a local area network (LAN) game server, listening for and managing connections from clients.
    
- **Key Properties & Settings:**
    
    - **Input (Start/Stop):** Flow control inputs to manually start or stop the server.
        
    - **Input (IP/Port):** The IP address and port number the server will use.
        
    - **Setting (On Startup):** If checked, the server starts automatically when the game begins.
        
    - **Output (On Start/Running/On Stop):** Flow control outputs that signal the server's state changes.
        
    - **Output (Server):** A reference to the server instance itself.
        
    - **Output (Received):** A flow control pulse that activates when new data arrives from any client.
        
    - **Output (Data):** The raw data that was received.
        
- **Practical Application:** Used by the "host" player in a multiplayer match. This node creates the game session that other players on the same network can then connect to.