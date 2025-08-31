- **Editor:** Logic Node Editor
    
- **Node Group:** Network
    
- **Core Function:** Converts complex game data (like vectors, dictionaries, or floats) into a standardized byte stream format that is suitable for network transmission.
    
- **Key Properties & Settings:**
    
    - **Input (Data):** The game data to be prepared for sending.
        
    - **Setting (Built-In):** A dropdown to select the appropriate serialization method for the data type.
        
    - **Output (Data):** The resulting serialized data packet.
        
- **Practical Application:** A mandatory prerequisite for Send Data. Before you can send a player's vector position, you must first run it through this node to serialize it. The receiver will then use Rebuild Data to reverse the process.