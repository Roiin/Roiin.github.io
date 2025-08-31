- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 6
    
- **Core Function:** Changes the material assigned to a specific material slot on an object at runtime.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The target object whose material will be changed.
        
    - **Input (Slot):** The integer index of the material slot to modify (starting from 0).
        
    - **Input (Material):** The new material to apply to the slot.
        
    - **Output (Done):** A flow control pulse that activates after the material is changed.
        
- **Practical Application:** Used for dynamic visual effects: making a sword glow by swapping to an emissive material, showing damage on a shield by switching to a "cracked" material, or making an object appear cloaked.