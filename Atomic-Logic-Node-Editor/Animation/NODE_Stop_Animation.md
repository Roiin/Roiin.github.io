- **Editor:** Logic Node Editor
    
- - **Node Group:** Animation
        
- **Core Function:** Stops a currently playing animation Action on a specified Object or Armature.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node to stop the animation.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Object (Socket):** The target object or armature.
        
    - **Animation Layer (Socket):** An integer input specifying which animation layer to stop. If 0, it may stop all layers.
        
- **Practical Application:** Used to interrupt or end an animation. For example, if a player is in a "Reload" animation and gets hit by an enemy, an event could trigger this node to stop the reload and allow a "HitStun" animation to play.