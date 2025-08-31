**Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 4 - Object Data
    
- **Core Function:** Swaps the mesh data of an object with another mesh, with options to transfer physics and display settings.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The target object whose mesh will be replaced.
        
    - **Input (Mesh):** The source object providing the new mesh data.
        
    - **Setting (Use Display):** If checked, transfers the display settings (e.g., wireframe, solid) from the source mesh.
        
    - **Setting (Use Physics):** If checked, transfers the physics settings (collision bounds, etc.) from the source mesh.
        
    - **Output (Done):** A flow control pulse that activates after the replacement is complete.
        
- **Practical Application:** Creating destructible objects (swapping a whole vase with a shattered version) or upgrading a character's weapon by replacing the weapon's mesh with a new one.