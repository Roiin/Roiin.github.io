- **Editor:** Logic Node Editor
    
- **Node Group:** Portals
    
- **Core Function:** Acts as a "wireless" receiver for a data connection within a node tree. It finds a corresponding Portal Out node (not pictured) with the same name and provides its data as an output. This is not a processing node but a powerful utility for organizing complex graphs.
    
- **Key Properties & Settings:**
    
    - **Setting (Portal Name):** A string name that acts as the "channel." It must exactly match the name of a Portal Out node elsewhere in the graph.
        
    - **Setting (Socket Type):** Defines the data type (Float, Vector, Object, etc.) that the portal will receive.
        
    - **Output (Value):** The data being sent from the corresponding Portal Out node.
        
- **Practical Application:** To dramatically improve the readability of a complex node graph. Instead of dragging a long connection ("noodle") from one side of the graph to the other, you can send the data from a Portal Out and receive it anywhere else with a Portal In node. This prevents visual clutter and allows for more modular and organized logic.