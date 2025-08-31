- **Editor:** Logic Node Editor
    
- - **Node Group:** Network
        
- **Core Function:** Establishes a connection from the local machine to a LAN game server.
    
- **Key Properties & Settings:**
    
    - **Input (Connect/Disconnect):** Flow control inputs to manually initiate or terminate a connection.
        
    - **Input (Server/Port):** The IP address and port number of the server to connect to.
        
    - **Setting (On Startup):** If checked, the client attempts to connect automatically.
        
    - **Output (On Connect/Connected/On Disconnect):** Flow control outputs that signal the client's connection state.
        
    - **Output (Client):** A reference to the client instance.
        
    - **Output (Received):** A flow control pulse that activates when new data arrives from the server.
        
    - **Output (Data):** The raw data that was received.
        
- **Practical Application:** Used by all "joining" players in a multiplayer match. They input the host's IP address and use this node to connect to the host's game session.