- **Editor:** Logic Node Editor
    
- **Node Group:** Network
    
- **Core Function:** Transmits data over the network. From a client, it sends to the server. From the server, it can broadcast to all clients.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the send operation.
        
    - **Input (Server / Client):** The network instance that is sending the data.
        
    - **Input (Data):** The serialized data packet to be sent.
        
    - **Input (Subject):** A string "header" to identify the type of data (e.g., "Player_Transform", "Fire_Weapon").
        
    - **Output (Done):** A flow control pulse that activates after the data is sent.
        
- **Practical Application:** The workhorse of multiplayer communication. A client continuously sends its character's position and actions to the server. The server then uses this node to broadcast that information to all other clients to keep everyone's game world synchronized.