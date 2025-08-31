- **Editor:** Logic Node Editor
    
- **Node Group:** UI
    
- **Core Function:** A universal "setter" node used to modify the properties of any existing widget at runtime.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the change.
        
    - **Input (Widget):** The specific UI widget (Button, Label, etc.) to be modified.
        
    - **Input (Visibility, etc.):** The property to be changed. The available properties likely change based on the connected widget type.
        
    - **Output (Done):** A flow control pulse that activates after the attribute is set.
        
- **Practical Application:** Dynamically changing the UI. For example, changing a Label's text to update a score, hiding a button (Visibility = false) that the player can no longer use, or changing a health bar's color based on the player's health.