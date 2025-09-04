- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Converts a mesh object into a curve object. It can either trace the mesh's edges to create open or closed paths, or it can create a separate, closed curve for the boundary of each individual face.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be converted.
        
    - **Selection (Socket - Input):** In 'Edges' mode, this Boolean edge selection determines which edges will be part of the final curves.
        
    - **Curve (Socket - Output):** The resulting curve geometry.
        
- **Practical Application:** This node is perfect for creating wireframe effects or generating paths from existing geometry, like creating glowing energy conduits running along the panel lines of a sci-fi animal.
    
    1. Start with your detailed sci-fi animal model. The model has distinct armor plates with beveled edges between them.
        
    2. **The Goal:** You want to create glowing tubes that perfectly trace these panel lines.
        
    3. **The Problem:** The panel lines are just edges on a mesh; they have no thickness and cannot be given an emissive material directly.
        
    4. **The Solution:**
        
        - First, you need to select only the "crease" edges between the panels. You can do this with an Edge Angle node, selecting all the concave (positive signed angle) edges.
            
        - Use the Mesh to Curve node on your animal. Feed your edge selection into the Selection input.
            
        - The output is now a curve object that is a perfect wireframe "skeleton" of your panel lines.
            
        - Now you can use Curve to Mesh with a small Curve Circle as the profile to turn this wireframe into a set of physical, renderable tubes.
            
        - Assign an emissive material to these tubes. The result is a network of glowing conduits that perfectly conforms to the armor plating of your creature.