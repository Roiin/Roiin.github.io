- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 6
    
- **Core Function:** Makes an object and optionally its entire hierarchy visible or invisible. The object still exists and processes logic, it just isn't rendered.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The target object.
        
    - **Input (Visible):** A boolean; true to make visible, false to make invisible.
        
    - **Setting (Include Children):** If checked, the visibility change also applies to all child objects.
        
    - **Output (Done):** A flow control pulse that activates after the visibility is set.
        
- **Practical Application:** Hiding a power-up inside a box until the box is broken, making a ghost character appear and disappear, or for performance optimization by hiding objects that are far from the camera.