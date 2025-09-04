- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Reverses the winding order of a face's vertices, which has the effect of flipping its normal to point in the opposite direction.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh whose faces will be flipped.
        
    - **Selection (Socket - Input):** A Boolean mask. Only faces where this is True will be flipped.
        
    - **Mesh (Socket - Output):** The mesh with its selected faces' normals flipped.
        
- **Practical Application:** This node is essential for the classic "inverted hull" cartoon outlining technique.
    
    1. Start with your main character model, for example, an animal.
        
    2. **The Goal:** You want to create a thick, black cartoon outline around the entire animal.
        
    3. Duplicate your animal's geometry. You will modify this duplicate to create the outline.
        
    4. Use a Set Position node on the duplicate. For the Offset, use the mesh's Normal vector, scaled by a small amount (e.g., 0.05). This inflates the duplicate mesh, making it slightly larger than the original.
        
    5. **The Problem:** At this point, the duplicate just looks like a slightly fatter version of the original.
        
    6. **The Solution:** Insert the Flip Faces node. This turns the entire inflated mesh "inside-out".
        
    7. Now, assign a simple, unlit black material to this flipped, inflated mesh. In the material settings, enable "Backface Culling".
        
    8. When you render the original animal and the outline object together, the inside-out faces of the outline are culled, but the "back" of those faces (which are now pointing inwards towards the original model) become visible. Because the outline mesh is slightly larger, this creates a perfect, consistent black border around the character's silhouette. The Flip Faces node is the critical step that makes this entire technique work.