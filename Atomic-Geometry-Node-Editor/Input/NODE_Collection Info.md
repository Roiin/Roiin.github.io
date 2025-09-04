- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Imports all objects from a specified Collection into the node tree, packaging them as a set of instances for procedural scattering or assembly.
    
- **Key Properties & Settings:**
    
    - **Collection (Socket - Input):** The source collection from which to import objects.
        
    - **Separate Children (Socket - Input):** A boolean. If True, each object within the collection is treated as an individual, separate instance. If False, the entire collection is treated as a single instance.
        
    - **Reset Children (Socket - Input):** A boolean. If True, it neutralizes the original transforms of the objects within the collection, placing them all at the origin of their instance. This is useful for precise placement.
        
    - **Transform Space (Property):** Determines how the transforms of the output instances are calculated, with 'Original' or 'Relative' options.
        
    - **Instances (Socket - Output):** The primary output, providing the objects from the collection as a list of usable instances.
        
- **Practical Application:** This is the primary method for creating varied instance scattering. For example, to create a diverse forest, you would first create a collection named "Forest_Assets" and place several different tree models inside it. In the Geometry Nodes setup, you use the Collection Info node, select "Forest_Assets," and check Separate Children. When you connect its Instances output to an Instance on Points node (with Pick Instance enabled), the system will randomly choose a different tree model for each point, resulting in a natural, mixed forest instead of a uniform one.