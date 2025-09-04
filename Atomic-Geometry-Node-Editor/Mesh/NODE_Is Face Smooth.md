- **Editor:** Geometry-Nodes-Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each face in a mesh, this node outputs a Boolean value that is True if the face is set to 'Shade Smooth' and False if it is set to 'Shade Flat'.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Smooth (Socket - Output):** A Boolean field on the Face domain. True for smooth-shaded faces, False for flat-shaded faces.
        
- **Practical Application:** This node is ideal for creating procedural setups that automatically adapt to the intended art style of a mesh, for example, a "Stylized Outliner" that draws lines only on the hard edges of a low-poly model.
    
    1. Imagine you have a character model that is a mix of smooth, organic parts (the face) and hard-surface, flat-shaded parts (the armor). The artist has already set the shading to 'Smooth' for the face and 'Flat' for the armor.
        
    2. **The Goal:** You want to procedurally generate a cartoon outline (e.g., using a "solidify-and-flip-normals" technique) only around the hard-surface armor pieces.
        
    3. Use the Is Face Smooth node. Its Smooth output will be False for all the armor faces.
        
    4. You can use this Boolean result (which is a selection for all flat-shaded faces) to Separate Geometry, isolating only the armor pieces.
        
    5. Now you can apply your outline effect only to this separated armor geometry.
        
    6. The result is an intelligent outliner that respects the artist's original shading intent, automatically applying the effect only to the parts of the model that are meant to look like hard surfaces.