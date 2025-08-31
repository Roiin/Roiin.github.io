- **Editor:** Logic Node Editor
    
- **Node Group:** Python
    
- **Core Function:** Sets or creates a custom attribute (Game Property) on any game object at runtime. This is the primary method for storing custom data on objects within the node system.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Object Instance):** The target object on which the attribute will be set.
        
    - **Input (Attribute):** A string for the name of the attribute (e.g., "health", "ammo", "isAlert").
        
    - **Input (Value):** The value to assign to the attribute. The data type can be changed (Float, Integer, String, etc.).
        
    - **Output (Done):** A flow control pulse that activates after the attribute has been set.
        
- **Practical Application:** The node-based equivalent of object['property'] = value. It's used to manage the state of any object: setting a character's health, storing the amount of ammo in a weapon, or flagging an enemy as alerted.