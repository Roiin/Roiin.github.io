- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 3 - Collections
    
- **Core Function:** Renders a specified collection in a separate scene pass, typically making it appear on top of the main scene.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Camera):** The camera from which the overlay collection will be viewed.
        
    - **Input (Collection):** The collection to be set as an overlay.
        
    - **Output (Done):** A flow control pulse that activates after the overlay is set.
        
- **Practical Application:** Commonly used for rendering 3D UI elements that should not be affected by in-game lighting or depth. Also essential for the classic "viewmodel" in a first-person shooter (the player's hands and weapon) to prevent them from clipping through walls.