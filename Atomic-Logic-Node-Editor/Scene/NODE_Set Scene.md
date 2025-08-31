- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 4
    
- **Core Function:** Changes the active scene, effectively loading a new level or menu.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Scene):** The scene to be loaded. This is often provided by a Get Scene node or by name.
        
    - **Output (Done):** A flow control pulse that activates after the scene transition begins.
        
- **Practical Application:** The core node for level transitions. Used when the player enters a portal to load the next area, to return to the main menu, or to load a "Game Over" screen.