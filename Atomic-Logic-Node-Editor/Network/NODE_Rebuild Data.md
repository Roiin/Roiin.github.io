- **Editor:** Logic Node Editor
    
- **Node Group:** Network
    
- **Core Function:** The inverse of Serialize Data. It takes a raw data packet received from the network and reconstructs it back into its original, usable game data type.
    
- **Key Properties & Settings:**
    
    - **Input (Data):** The raw data from the Received socket of a server or client node.
        
    - **Setting (Built-In):** A dropdown to select the de-serialization method, which must match the method used by the sender.
        
    - **Output (Data):** The reconstructed, usable game data (e.g., a vector, a float, a string).
        
- **Practical Application:** A mandatory step after receiving network data. When data with the subject "Player_Transform" is received, it is fed into this node to turn it back into a vector, which can then be used to update a character's position.