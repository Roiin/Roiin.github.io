- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Set Bone Data
    
- **Core Function:** Sets the "Inherit Rotation" property for a specified bone, enabling or disabling whether it rotates with its parent.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Armature (Socket):** The armature object.
        
    - **Bone Name (Selector):** A dropdown to select the specific bone.
        
    - **Bool (Socket):** A boolean input. True enables inheritance, False disables it.
        
- **Practical Application:** Allows for creating dynamic constraints. You could disable rotation inheritance for a character's head bone while they are targeting an enemy, allowing the head to track the target independently of the body's animation, and then re-enable it afterwards.