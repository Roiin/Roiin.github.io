- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Increases the resolution of a mesh by splitting each face into smaller faces. This is a simple subdivision that does not smooth the mesh or change its overall shape. It is the procedural equivalent of the "Subdivide" operator in Edit Mode.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):-** The source mesh to be subdivided.
        
    - **Level (Socket - Input):** An integer controlling the number of subdivision iterations. A level of 1 splits each quad into four smaller quads. A level of 2 splits those quads again, resulting in 16 total, and so on.
        
    - **Mesh (Socket - Output):** The new, higher-resolution mesh.
        
- **Practical Application:** This node is essential for preparing low-poly geometry for high-frequency displacement effects, like creating the detailed scales on an animal's skin.
    
    1. Start with your base, low-poly animal model.
        
    2. **The Goal:** You want to use a procedural noise or a scale texture to displace the mesh and create the fine, bumpy texture of scales or rough hide.
        
    3. **The Problem:** The base mesh doesn't have enough vertices. If you apply a displacement map to it, you will just get jagged, low-resolution spikes. You need more geometry for the detail to be visible.
        
    4. **The Solution:** Insert a Subdivide Mesh node before your displacement logic (e.g., a Set Position node driven by a Noise Texture).
        
    5. Set the Level to a value like 3 or 4. This will add thousands of new vertices, creating a dense mesh.
        
    6. Now, when you apply the Set Position node with your noise texture, there is enough geometric resolution to capture the fine details of the noise. The result is a smooth, high-frequency bumpy texture that looks like realistic animal skin, which would have been impossible without first increasing the mesh density with Subdivide Mesh.