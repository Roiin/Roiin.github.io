- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Material (Write/Assign)
    
- **Core Function:** Assigns a specified Material to the selected faces of a mesh. If the material is not already in the object's material slots, this node will add it.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry to be modified.
        
    - **Selection (Socket - Input):** A boolean field on the Face domain. The new material will only be applied to faces where this is True.
        
    - **Material (Socket - Input):** The material to be assigned, provided by a Material input node.
        
    - **Geometry (Socket - Output):** The geometry with the new material assignments.
        
- **Practical Application:** This node is fundamental for any workflow that involves generating geometry with multiple textures. Imagine you are creating a procedural lizard where the back and belly have different scale patterns.
    
    1. Start with your lizard mesh.
        
    2. **The Goal:** To apply a "Back_Scales" material to the top-facing parts and a "Belly_Scales" material to the bottom-facing parts.
        
    3. First, you need a selection to separate the top from the bottom. You can do this by taking the Normal of each face and comparing its Z component to zero using a Compare node. Faces with a positive Z normal are on top.
        
    4. Use two Set Material nodes:
        
        - The first node uses the "top" selection. You connect your "Back_Scales" material to its Material input.
            
        - The second node uses an inverted version of the "top" selection (using a Boolean Math 'Not' node). You connect your "Belly_Scales" material to its Material input.
            
    5. **The Result:** Your lizard model is now procedurally textured. The material assignment is based on the geometric orientation of its faces. If you were to change the lizard's pose, the material boundary would intelligently and automatically update to follow the new "top" and "bottom" surfaces.