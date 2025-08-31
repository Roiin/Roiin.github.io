- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 2 - Post FX
    
- **Core Function:** Enables or disables an already added filter without removing it from the render stack. This is more efficient than repeatedly adding and removing filters.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Pass Index):** The integer index of the target filter.
        
    - **Input (Active):** A Boolean value; true activates the filter, false deactivates it.
        
    - **Output (Done):** A flow control pulse that activates after the state is changed.
        
- **Practical Application:** Perfect for frequently toggled effects. For instance, a "detective vision" mode could be added once at the start of a level (e.g., at Pass Index 5) and then this node is used to simply toggle its Active state on and off as needed.