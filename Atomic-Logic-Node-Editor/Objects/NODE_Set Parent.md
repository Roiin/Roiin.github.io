- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 6
    
- **Core Function:** Establishes a parent-child relationship between two objects. The child object will inherit the transforms (location, rotation, scale) of the parent.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Child Object):** The object that will become the child.
        
    - **Input (Parent Object):** The object that will become the parent.
        
    - **Output (Done):** A flow control pulse that activates after the relationship is set.
        
- **Practical Application:** Essential for picking up items (parenting the item to the character's hand), having a character ride a moving platform (parenting the character to the platform), or attaching a torch to a wall.