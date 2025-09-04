- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Scales individual or connected groups of faces and edges in place, relative to a specified center point. This is the procedural equivalent of the "Inset Faces" tool's individual mode or scaling elements around their individual origins.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source mesh to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. Only selected elements will be scaled.
        
    - **Scale (Socket - Input):** The scaling factor. A value of 0.9 would shrink the element by 10%.
        
    - **Center (Socket - Input):** The pivot point for the scaling operation. To scale faces in place, this should be their own center position.
        
    - **Domain (Property):** The element type to scale: Faces or Edges.
        
    - **Scale Mode (Property):**
        
        - **Uniform:** Scales equally in all directions.
            
        - **Single Axis:** Scales along a specific Axis vector.
            
    - **Geometry (Socket - Output):** The mesh with its elements scaled.
        
- **Practical Application:** This node is perfect for creating sci-fi paneling on the armor of a mechanical animal.
    
    1. Start with a base mesh for the armor plating, made up of many quad faces.
        
    2. **The Goal:** You want to turn each quad face into a beveled panel with a visible seam between it and its neighbors.
        
    3. Use the Scale Elements node with the Domain set to 'Face'.
        
    4. Set the Scale to a value slightly less than 1.0, for example, 0.95. This will shrink every face in place, creating a small gap between them.
        
    5. The result of this first step is a set of disconnected, floating panels.
        
    6. To connect them, you can use an Extrude Mesh node on the original armor geometry (before the scaling) to create a slightly thicker base layer.
        
    7. You can then Join Geometry with your scaled panels, placing them on top of the extruded base.
        
    8. The final result is a detailed surface that appears to be constructed from many individual plates with visible seams between them, all created from a simple base mesh. This is a classic technique for adding greebles and surface detail.