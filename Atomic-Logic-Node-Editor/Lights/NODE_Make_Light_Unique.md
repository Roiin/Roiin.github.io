- **Editor:** Logic Node Editor
    
- **Node Group:** Lights
    
- **Core Function:** Converts an instanced (duplicated) light into a unique light with its own data-block.
    
- **System Note:** When you duplicate a light in Blender (Alt+D), it creates an instance that shares the same light data. Changes to one will affect all its instances. This node breaks that link for the specified light.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control output.
        
    - **Condition (Socket):** A Boolean input.
        
    - **Light Object (Socket):** The target instanced Light object that you want to make unique.
        
    - **Light (Socket):** An output providing a reference to the now-unique light object.
        
- **Practical Application:** A crucial utility for procedural generation or runtime object spawning. If you spawn multiple copies of a "Torch" prefab, you would immediately run this node on each new torch so that you can control their individual colors and brightness (e.g., for unique flickering effects) without affecting all other torches.