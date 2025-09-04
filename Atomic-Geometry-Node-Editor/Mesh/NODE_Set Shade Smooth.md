- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Write)
    
- **Core Function:** Procedurally sets the shading of faces or edges to be either 'Smooth' or 'Flat'. This is the procedural equivalent of the "Shade Smooth" and "Shade Flat" operators in Object Mode.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The mesh geometry whose shading will be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. The shading will only be changed on elements where this is True.
        
    - **Shade Smooth (Socket - Input):** A Boolean value. If True, the selected elements are set to smooth. If False, they are set to flat.
        
    - **Domain (Property):** A toggle to choose whether you are modifying the shading of Faces or marking Edges as sharp/smooth.
        
    - **Mesh (Socket - Output):** The mesh with the updated shading attributes.
        
- **Practical Application:** This node is perfect for creating hybrid models that combine organic and hard-surface elements, like a cyborg animal.
    
    1. Imagine you have a model of an animal, and you use a procedural technique (like a Geometry Proximity to a "cybernetics" object) to select a region of its face to be replaced with a metal plate.
        
    2. You Separate Geometry based on this selection. One part is the organic skin, the other is the future metal plate.
        
    3. **The Goal:** You want the organic skin to be smoothly shaded, while the metal plate has a distinct, faceted, low-poly look.
        
    4. Use two Set Shade Smooth nodes:
        
        - On the "organic skin" geometry stream, use a Set Shade Smooth node with the Shade Smooth Boolean set to True.
            
        - On the "metal plate" geometry stream, use another Set Shade Smooth node with the Shade Smooth Boolean set to False.
            
    5. Join Geometry to combine them back together.
        
    6. **The Result:** You have a single, continuous mesh where different parts have different shading styles. The skin will render with smooth, soft highlights, while the cybernetic plate will have a hard-edged, faceted appearance, clearly distinguishing the two surface types and reinforcing the visual design.