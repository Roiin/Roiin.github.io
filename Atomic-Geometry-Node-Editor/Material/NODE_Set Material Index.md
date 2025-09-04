- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Material (Write/Assign)
    
- **Core Function:** Assigns a material to the selected faces of a mesh by directly setting the material_index attribute. This requires you to know the integer slot number of the material you want to assign.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry to be modified.
        
    - **Selection (Socket - Input):** A boolean field on the Face domain. The material index will only be set on faces where this is True.
        
    - **Material Index (Socket - Input):** An integer field providing the material slot number to assign (0 for the first material, 1 for the second, etc.).
        
    - **Geometry (Socket - Output):** The geometry with the new material index assignments.
        
- **Practical Application:** This node is useful for creating patterns or assignments based on mathematical functions. Imagine you have a creature with a segmented shell, like a pillbug, and you want to assign alternating materials to the segments.
    
    1. First, you create the segmented shell. The faces of each segment can be assigned a unique Mesh Island index.
        
    2. **The Goal:** You want to assign "Shell_Material_A" (in slot 0) to the even-numbered segments and "Shell_Material_B" (in slot 1) to the odd-numbered segments.
        
    3. Use the Mesh Island node to get the Island Index for each face.
        
    4. Use a Math node set to 'Modulo 2' on the Island Index. The output of this will be 0 for all even-numbered islands and 1 for all odd-numbered islands.
        
    5. Connect this Modulo output directly into the Material Index input of the Set Material Index node.
        
    6. **The Result:** The node will set the material index to 0 for all the even segments and 1 for all the odd segments, perfectly creating the alternating material pattern. This is a very efficient, low-level way to achieve the effect without needing to create intermediate selections for each material.