- **Editor:** Logic Node Editor
    
- **Node Group:** UI
    
- **Core Function:** Creates a container widget used to group and organize other UI elements. It helps in structuring the UI hierarchically.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the layout to be created and displayed.
        
    - **Input (Parent):** The parent widget, which is usually the Canvas or another Layout.
        
    - **Input (X, Y, Angle):** The position and rotation of the layout.
        
    - **Input (Relative Position / Size):** Crucial inputs (vectors of 0.0-1.0) that position and scale the layout relative to its parent's dimensions. This is key for creating resolution-independent UI.
        
    - **Output (Layout):** The reference to the created layout widget.
        
- **Practical Application:** Used to create panels or sections. For example, a "Player_Info" layout in the top-left of the screen that will contain the player's health bar and portrait.