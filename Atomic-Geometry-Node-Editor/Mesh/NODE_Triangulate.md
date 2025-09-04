- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Converts all quads and N-gons in a mesh into triangles. This is the procedural equivalent of the Triangulate tool in Edit Mode and ensures that all faces in the mesh are of the simplest possible type.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be triangulated.
        
    - **Selection (Socket - Input):** A Boolean mask. Only faces where this is True will be triangulated.
        
    - **Quad Method (Property):** A dropdown to control how four-sided faces are split. 'Shortest Diagonal' is often a good default, while 'Beauty' can produce more evenly shaped triangles at a performance cost.
        
    - **N-gon Method (Property):** A dropdown to control how faces with more than four sides are split.
        
    - **Mesh (Socket - Output):** The new, fully triangulated mesh.
        
- **Practical Application:** This node is crucial for creating certain artistic styles, like a "low-poly" faceted look for an animal model, and for preparing a mesh for operations that require triangular faces.
    
    1. Start with a smooth, organic animal model created with a Subdivision Surface node.
        
    2. **The Goal:** You want to transform this smooth model into a stylized, faceted object that looks like it's carved from crystal.
        
    3. **The Problem:** The smooth mesh doesn't have the sharp, flat planes needed for a crystalline look.
        
    4. **The Solution:**
        
        - First, you might want to simplify the mesh. Use a Decimate Geometry node to reduce the polygon count. This creates a mix of quads and triangles.
            
        - Next, insert the Triangulate node. This ensures that every face on the model is now a triangle.
            
        - Finally, insert a Set Shade Smooth node with the Shade Smooth Boolean set to False. This tells Blender to render each triangular face as a distinct, flat plane.
            
    5. The result is a complete stylistic transformation. The smooth, organic animal is now a hard-surface, faceted statue. The Triangulate node was the key step to ensure that every face was a simple plane, which is essential for achieving the faceted, low-poly aesthetic.