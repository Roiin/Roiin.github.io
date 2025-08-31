- **Editor:** Logic Node Editor
    
- **Node Group:** Animation
    
- **Core Function:** Retrieves the current status of an animation Action on a specified Object or Armature.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The target object or armature to query.
        
    - **Layer (Socket):** An integer input for the animation layer to check.
        
    - **Is Playing (Socket):** A boolean output that is True if an animation is currently playing on the specified layer.
        
    - **Action Name (Socket):** A string output that provides the name of the currently playing Action.
        
    - **Action Frame (Socket):** A float output that provides the current playback frame of the Action.
        
- **Practical Application:** Used to query the animation state to make logical decisions. For example, preventing a player from attacking again if the Action Name output is already "Attack_01", effectively stopping animation spam.