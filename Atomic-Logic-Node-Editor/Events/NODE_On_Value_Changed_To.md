- **Editor:** Logic Node Editor
- **Node Group:** Events
    
- **Core Function:** Monitors an input value and triggers a logic pulse only when that value becomes equal to a specific target value.
    
- **Key Properties & Settings:**
    
    - **Value (Socket):** The data input (e.g., Bool, String, Integer, Float) to be monitored.
        
    - **Result (Socket):** The target value that the Value input is compared against.
        
    - **Type (Dropdown):** Defines the data type for the Value and Result sockets. Options include Bool, String, Float, Integer, File Path.
        
    - **Out (Socket):** The flow control output that pulses when Value equals Result.
        
- **Practical Application:** Used to trigger an event when a specific condition is met. Example: When a "KeysCollected" integer property changes to 3, this node triggers the "UnlockFinalDoor" event. When a "QuestActive" Boolean becomes True, it triggers the associated logic.