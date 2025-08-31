- **Editor:** Logic Node Editor
    
- - **Node Group:** Scene Part 3 - Collections
        
- **Core Function:** Removes a collection from the overlay render pass, returning it to the normal scene rendering.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Collection):** The collection to be removed from the overlay state.
        
    - **Output (Done):** A flow control pulse that activates after the overlay is removed.
        
- **Practical Application:** Used to hide a 3D UI or viewmodel when it's no longer needed, such as when entering a cinematic or a menu screen.