- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 2 - Post FX
    
- **Core Function:** Removes an active 2D post-processing filter from the render stack based on its index.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Pass Index):** The integer index of the filter to remove.
        
    - **Output (Done):** A flow control pulse that activates after the filter is removed.
        
- **Practical Application:** Used to permanently disable a visual effect, such as removing a "poisoned" screen vignette after the player uses an antidote.