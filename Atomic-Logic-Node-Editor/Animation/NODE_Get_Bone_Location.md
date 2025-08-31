- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Get Bone Data
    
- **Core Function:** Retrieves the location (position) of a bone's head in world space.
    
- **Key Properties & Settings:**
    
    - **Armature (Socket):** The armature object.
        
    - **Bone Name (Selector):** A dropdown to select the bone.
        
    - **Location (Socket):** A 3D vector output representing the bone head's world coordinates.
        
- **Practical Application:** Essential for attaching objects or effects to a moving character. For example, to place a weapon in a character's hand, you would get the location of the "Hand.R" bone and continuously set the weapon's position to that vector.