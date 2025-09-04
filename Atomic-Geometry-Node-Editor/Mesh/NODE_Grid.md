- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a flat, rectangular grid mesh aligned to the XY plane.
    
- **Key Properties & Settings:**
    
    - **Size X / Size Y (Sockets - Input):** Floats that control the dimensions of the grid.
        
    - **Vertices X / Vertices Y (Sockets - Input):** Integers that control the number of subdivisions along each axis, determining the grid's resolution.
        
    - **Mesh (Socket - Output):** The generated grid mesh.
        
    - **UV Map (Socket - Output):** A default, perfectly unwrapped UV map that fills the 0-1 UV space, ready to be stored as an attribute for texturing.
        
- **Practical Application:** The Grid is the quintessential starting point for creating procedural landscapes or the skin of an animal through displacement.
    
    1. **The Goal:** To create a patch of rough, scaly dragon skin.
        
    2. **The Base:** Start with a Grid node. Set a high Vertices count (e.g., 128x128) to create a dense mesh with enough resolution to hold fine details.
        
    3. **The Displacement:** Use a Set Position node on the grid. For the Offset input, you'll use a texture.
        
    4. Use a Noise Texture node, or for more specific scale-like patterns, a Voronoi Texture set to 'Distance to Edge'.
        
    5. To make the displacement happen perpendicular to the surface (straight up), multiply the texture's Factor output by the grid's Normal vector (using a Vector Math 'Scale' node).
        
    6. Connect this final vector to the Offset socket of the Set Position node.
        
    7. **The Result:** The flat grid is displaced by the texture, creating a complex, bumpy surface that looks like a patch of detailed dragon skin. This can then be deformed and wrapped around a base animal model using a Surface Deform modifier. The Grid provided the essential, high-resolution, and perfectly UV-mapped canvas for the procedural texture to "paint" on.