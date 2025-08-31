- **Editor:** Logic Node Editor
    
- **Node Group:** UI
    
- **Core Function:** Changes the appearance of the mouse cursor.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the change.
        
    - **Input (Image):** An image object (from a Get Image node) to use as the new cursor.
        
    - **Input (Size):** A vector to define the width and height of the cursor.
        
    - **Output (Done):** A flow control pulse that activates after the cursor is changed.
        
- **Practical Application:** Changing the cursor contextually. For example, showing a hand icon when hovering over an interactive object, a sword icon when hovering over an enemy, or a custom crosshair.