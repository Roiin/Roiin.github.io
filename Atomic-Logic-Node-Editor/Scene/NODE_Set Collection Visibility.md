- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 3 - Collections
    
- **Core Function:** Sets the visibility for all objects within a specified collection, effectively hiding or showing them all at once.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Input (Collection):** The target collection.
        
    - **Input (Visible):** A Boolean; true makes the collection's objects visible, false makes them invisible.
        
    - **Setting (Include Children):** If checked, the visibility change also applies to any nested sub-collections.
        
    - **Output (Done):** A flow control pulse that activates after the visibility is set.
        
- **Practical Application:** A key optimization technique. Used for level streaming (hiding collections that are far away) or for toggling entire groups of related objects, like showing/hiding the interior of a building when the player enters/exits.