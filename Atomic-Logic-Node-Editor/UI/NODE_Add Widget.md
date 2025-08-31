- **Editor:** Logic Node Editor
    
- **Node Group:** UI
    
- **Core Function:** Dynamically parents an existing widget to a container widget (like a Layout).
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Parent):** The container widget (e.g., a Layout) that will receive the new child.
        
    - **Input (Widget):** The widget to be added.
        
    - **Output (Done):** A flow control pulse that activates after the widget is added.
        
- **Practical Application:** Building dynamic lists. When a player picks up an item, you would Create Image for its icon and then use Add Widget to add that icon to the "Inventory_Panel" layout.