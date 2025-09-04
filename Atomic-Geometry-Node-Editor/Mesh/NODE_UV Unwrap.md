- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (UV)
    
- **Core Function:** Generates a new UV map by procedurally cutting a mesh along designated 'seam' edges, flattening the resulting shells, and automatically packing them into the 0-1 UV space. This is the procedural equivalent of the 'Unwrap' operator in the UV Editor.
    
- **Key Properties & Settings:**
    
    - **Selection (Socket - Input):** A boolean face selection. Filters which faces will be included in the unwrap operation.
        
    - **Seam (Socket - Input):** A boolean edge selection. This is the most critical input, defining the 'cuts' for the unwrap. The mesh is virtually torn along these edges to create the UV islands.
        
    - **Margin (Socket - Input):** A float that controls the empty space left between the packed UV islands.
        
    - **Method (Property):** The algorithm used for unwrapping ('Angle Based' or 'Conformal'). 'Angle Based' is generally preferred for complex shapes.
        
    - **UV (Socket - Output):** The primary output; a 2D vector field representing the new UV coordinates.
        
- **Practical Application:** This node is essential for creating a clean, non-overlapping UV map for a procedurally generated creature, like a lizard, so it can be textured correctly.
    
    1. **The Goal:** To automatically generate a high-quality UV map for your lizard model, which might be generated from primitives and procedural operations.
        
    2. **The Problem:** The creature is generated on the fly, so you can't manually mark seams in Edit Mode. A default UV map would be distorted and unusable for texturing.
        
    3. **The Solution:**
        
        - First, you need to define the seams procedurally. A great way to do this is by finding the sharpest edges. Use the Edge Angle node.
            
        - Use a Compare node to create a Boolean selection for all edges where the Unsigned Angle is greater than a certain threshold (e.g., 1.05 radians, or ~60 degrees). This effectively selects all the hard corners and creases of the model.
            
        - Feed this edge selection directly into the Seam input of the UV Unwrap node.
            
    4. **Crucial Final Step:** The UV output from the node is now a new, clean UV map. To make Blender recognize this as a usable UV map for your shader, you **must** use a Store Named Attribute node.
        
        - Set its Domain to **Face Corner**.
            
        - Set its Data Type to **Vector** (which will be treated as a 2D Vector in this context).
            
        - Give it a name, for example, "procedural_uv".
            
    5. **The Result:** You now have a creature with a high-quality, automatic UV map. In the Shader Editor, you can use an Attribute node to access "procedural_uv" and correctly apply your scale textures or other image maps. The entire UVing process is now part of your non-destructive, procedural workflow.