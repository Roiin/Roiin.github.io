- **Editor:** Geometry Node Editor
    
- **Node Group:** Attribute
    
- **Core Function:** Evaluates a field and stores the resulting data on a geometry as a persistent, named attribute. This makes the data accessible outside the current node tree, such as in the shader editor, by other modifiers, or through scripting.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The target geometry where the attribute will be stored.
        
    - **Selection (Socket - Input):** A boolean field that acts as a mask, only storing the new attribute value on elements (points, faces, etc.) where the selection is True.
        
    - **Value (Socket - Input): ** The data field to be evaluated and stored.
        
    - **Name (Socket - Input):** A string that defines the public name of the attribute. This name will be used to access the data elsewhere.
        
    - **Domain (Property):** The attribute domain (e.g., Point, Face, Edge) where the data will be stored.
        
    - **Data Type (Property):** The type of data being stored (e.g., Vector, Float, Color, Boolean).
        
    - **Geometry (Socket - Output):** The modified geometry, now containing the new or updated named attribute.
        
- **Practical Application:** This is the primary method for creating procedural data that drives materials. **Example:** Create a procedural "wear mask" based on edge sharpness or ambient occlusion within Geometry Nodes. Use Store Named Attribute to save this mask with the name "wear_amount". In the Shader Editor, use an Attribute node to retrieve "wear_amount" and use it as a factor to mix between a pristine metal shader and a rusted/damaged metal shader, creating highly detailed and context-aware assets automatically.