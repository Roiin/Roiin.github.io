- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Applies a transformation (translation, rotation, and/or scale) to an entire block of geometry as a single unit. This is distinct from the Set Position node, which moves individual points, and the instance transform nodes, which affect individual instances.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry to be transformed.
        
    - **Translation (Socket - Input):** A vector that moves the entire geometry.
        
    - **Rotation (Socket - Input):** An Euler value that rotates the entire geometry around its origin.
        
    - **Scale (Socket - Input):** A vector that scales the entire geometry.
        
    - **Mode (Property):** Allows you to switch between providing Components (separate Translation, Rotation, Scale) or a single Matrix for the transformation.
        
    - **Geometry (Socket - Output):** The geometry after the transformation has been applied.
        
- **Practical Application:** This node is essential for modular construction, where you build parts separately and then assemble them. Imagine you are procedurally creating a tree.
    
    1. First, you create a complex, detailed branch as its own separate geometry stream. It's easiest to design this branch centered at the world origin (0,0,0), growing along the Y-axis.
        
    2. Separately, you have your main tree trunk geometry.
        
    3. To attach the branch to the trunk, you use the Transform Geometry node on the entire branch geometry.
        
    4. You can then use the Translation input to move the branch's starting point up along the trunk, and the Rotation input to angle it outwards in a natural-looking way.
        
    5. You can repeat this process, creating several copies of your branch geometry and using a different Transform Geometry node for each one to place it uniquely.
        
    6. Finally, you use a Join Geometry node to combine the trunk with all of your individually transformed branches, resulting in a single, complete tree mesh. This modular approach is far more organized and manageable than trying to build the entire tree in one go.