- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a cylinder-shaped mesh primitive.
    
- **Key Properties & Settings:**
    
    - **Vertices (Socket - Input):** The number of vertices in the top and bottom circles, controlling the roundness of the cylinder. A value of 4 would create a square pillar.
        
    - **Side Segments (Socket - Input):** The number of vertical edge loops along the cylinder's height.
        
    - **Fill Segments (Socket - Input):** The number of concentric edge loops used to fill the caps.
        
    - **Radius (Socket - Input):** The radius of the cylinder.
        
    - **Depth (Socket - Input):** The height of the cylinder.
        
    - **Fill Type (Property):** Determines if the top/bottom are left open ('None'), filled with a single N-gon, or filled with a fan of triangles.
        
    - **Mesh (Socket - Output):** The generated cylinder mesh.
        
    - **Top / Side / Bottom (Sockets - Output):** Boolean selections for the faces of the corresponding parts of the cylinder, useful for assigning materials.
        
- **Practical Application:** The Cylinder is the perfect base for creating procedural tree trunks or the legs of a large animal like an elephant.
    
    1. **The Base:** Start with a Cylinder node. Set a high Vertices count (e.g., 16) for a round look and a high Side Segments count (e.g., 10) to provide enough geometry for deformation.
        
    2. **The Shape:** To make the trunk or leg look more organic, you need to break up its perfect shape.
        
        - **Tapering:** You can use a Set Position node and scale the X and Y components of the Position based on the Z-position to make the trunk wider at the bottom and thinner at the top.
            
        - **Noise:** Use another Set Position node. For the Offset, use a Noise Texture. This will add a bumpy, irregular surface to the cylinder, making it look more like natural bark or skin.
            
    3. **The Materials:** The Top, Side, and Bottom outputs are great for this. You can use the Side selection to assign a "Bark" or "Elephant Skin" material, while the Top selection could be a "Cut Wood" or "Flesh" material for a sawn-off tree or a dismembered limb.
        
    4. **The Result:** A simple, perfect Cylinder is transformed into a complex, organic form. The primitive provides the basic volume, and subsequent procedural operations add the necessary detail and realism.