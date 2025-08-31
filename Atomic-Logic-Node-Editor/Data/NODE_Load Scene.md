- **Editor:** Logic Node Editor
    
- **Node Group:** Data Part 3
    
- **Core Function:** An action node used to add, remove, or manage scenes within the running game instance. It is more advanced than the simpler Set Scene node.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the scene operation.
        
    - **Input (Scene):** A reference to the scene to be managed.
        
    - **Output (Loaded, Updated, Status, Datatype, Item):** These outputs likely provide detailed feedback about the state of the scene loading process, useful for creating loading screens or managing asynchronous operations.
        
- **Practical Application:** This node is essential for advanced scene management, such as additively loading a new scene on top of the current one (e.g., loading a UI scene) or asynchronously loading the next level in the background while the player is still in the current one to hide loading times.