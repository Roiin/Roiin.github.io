- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** A simplified and continuous version of Align Axis to Vector. It rotates an object to constantly "look at" a target object's origin.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The object that will perform the looking.
        
    - **Target (Socket):** The object to be looked at.
        
    - **Axis (Dropdown):** The local axis of the Object that should point towards the Target.
        
- **Practical Application:** A very common node for AI and interactive objects. Used to make an enemy's head track the player, to make a sunflower object always face a "sun" lamp, or to ensure a billboard-style sprite always faces the camera.