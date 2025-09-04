- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Material
    
- **Core Function:** Finds all instances of an Old material on a mesh and replaces them with a New material. This is a highly efficient way to swap materials procedurally.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source mesh geometry whose materials will be modified.
        
    - **Old (Socket - Input):** The material to be replaced. This is selected via a Material input node.
        
    - **New (Socket - Input):** The material that will take the place of the old one.
        
    - **Geometry (Socket - Output):** The geometry with the swapped materials.
        
- **Practical Application:** This node is perfect for creating seasonal variations for a procedural asset, like a tree.
    
    1. **The Setup:** You have a procedural tree where the leaves have a material called "Green_Leaves".
        
    2. **The Goal:** You want to add a simple "Season" slider (e.g., in the modifier panel) that can change the leaves to an autumn color.
        
    3. **The Materials:** You create a second material called "Autumn_Leaves".
        
    4. **The Node Tree:**
        
        - Use a Switch node. The Switch input can be a boolean from your modifier panel labeled "Is Autumn?".
            
        - The True input of the switch will be the "Autumn_Leaves" material.
            
        - The False input will be the "Green_Leaves" material.
            
        - Use a Replace Material node. The Old material is always "Green_Leaves".
            
        - The New material is the output of your Switch node.
            
    5. **The Result:** You have a non-destructive material switcher. When "Is Autumn?" is unchecked, the Switch outputs "Green_Leaves", so the node tries to replace "Green_Leaves" with "Green_Leaves", and nothing changes. When you check the box, the Switch outputs "Autumn_Leaves", and the node instantly swaps all the green leaf materials for the autumn ones. This is a very efficient way to manage material variations.