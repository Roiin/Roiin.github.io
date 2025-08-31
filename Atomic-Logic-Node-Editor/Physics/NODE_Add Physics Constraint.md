- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 3
    
- **Core Function:** Creates a new physics constraint (joint) between two objects at runtime.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Object):** The object to which the constraint will be added.
        
    - **Input (Target):** The other object involved in the constraint.
        
    - **Setting (Ball, etc.):** A dropdown to select the type of constraint (Hinge, Point, etc.).
        
    - **Output (Done):** A flow control pulse that activates after the constraint is added.
        
- **Practical Application:** Dynamically connecting objects, such as a grappling hook attaching to a wall or a character grabbing a ledge.