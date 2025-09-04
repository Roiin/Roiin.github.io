- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** Analyzes a mesh and identifies its "islands"—groups of connected vertices, edges, and faces that are not physically connected to other groups. It outputs a unique index for each island.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Island Index (Socket - Output):** An integer field. All vertices belonging to the same contiguous mesh island will share the same unique index.
        
    - **Island Count (Socket - Output):** A single integer value representing the total number of separate islands found in the mesh.
        
- **Practical Application:** This node is essential for applying varied effects to the separate components of a "kitbashed" model, such as the different armor plates on an animal.
    
    1. Imagine you've created a suit of armor for an animal by placing several separate mesh objects (a chest plate, shoulder pads, a helmet) and then joining them into a single object in Edit Mode. They are one object, but topologically, they are separate islands.
        
    2. **The Goal:** You want to give each separate armor plate a slightly different, random metallic color to suggest they were crafted at different times.
        
    3. **The Problem:** A standard Random Value node will assign a random color to every single face, creating a chaotic, confetti-like result.
        
    4. **The Solution:**
        
        - Use the Mesh Island node. The Island Index output will be 0 for all faces on the chest plate, 1 for all faces on the helmet, 2 for one shoulder pad, and so on.
            
        - Feed this Island Index into the ID socket of a Random Value node.
            
        - The Random Value node will now generate a single, consistent random color for each unique island index.
            
    5. Store this color as a named attribute and use it in your shader. The result is that the entire chest plate will be one random color (e.g., dark steel), the helmet will be another (e.g., bronze), and the shoulder pads will be a third, creating a much more natural and believable sense of variation.