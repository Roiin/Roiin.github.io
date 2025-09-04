- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Grease Pencil (Operations)
    
- **Core Function:** Converts Grease Pencil strokes into standard 3D curve objects. This is the primary bridge for applying all of Blender's powerful curve-based procedural modeling tools to 2D drawings.
    
- **Key Properties & Settings:**
    
    - **Grease Pencil (Socket - Input):** The source Grease Pencil geometry.
        
    - **Selection (Socket - Input):** A boolean mask to select which layers to convert.
        
    - **Curves (Socket - Output):** The resulting curve geometry. By default, each Grease Pencil layer is output as a separate instance containing curves.
        
- **Practical Application:** This node is essential for creating 3D objects from 2D sketches. Imagine you've drawn the outline of a detailed fantasy sword in Grease Pencil.
    
    1. **The Goal:** You want to turn this flat 2D drawing into a full 3D model.
        
    2. Use the Grease Pencil to Curves node. The output is now a standard 3D curve object that perfectly matches your drawing.
        
    3. You can now use all the curve operations we've documented. For example:
        
        - Use a Fill Curve node to create a solid 2D mesh of the sword's silhouette.
            
        - Use an Extrude Mesh node on the result to give the sword thickness.
            
        - Use a Separate Geometry node on the original curves (based on which layer you drew the "blade" vs. the "hilt" on) to apply different materials or bevels to different parts.
            
    4. This workflow allows an artist to quickly sketch a complex shape in 2D and then procedurally "inflate" it into a 3D model, which is often a much faster and more intuitive process than traditional 3D box modeling.