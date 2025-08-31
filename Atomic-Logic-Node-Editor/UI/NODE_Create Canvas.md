- **Editor:** Logic Node Editor
    
- **Node Group:** UI
    
- **Core Function:** Creates the root container for all 2D UI elements in the scene. It is the base layer upon which all other widgets are built.
    
- **Key Properties & Settings:**
    
    - **Setting (Start Preview):** A checkbox for in-editor debugging, allowing you to see the UI layout without running the game.
        
    - **Output (Canvas):** The most important output; this is the reference to the canvas object that must be used as the Parent for top-level UI elements like layouts and panels.
        
    - **Output (On Init):** A flow control pulse that activates exactly once, when the canvas is first created.
        
    - **Output (Done):** A continuous flow control pulse that is active as long as the canvas exists.
        
- **Practical Application:** The absolute first step in building any UI. You create one canvas to serve as the foundation for a main menu, a player HUD, or an inventory screen.