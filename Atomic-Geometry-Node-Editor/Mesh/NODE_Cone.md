- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a cone-shaped mesh primitive, with options to control its resolution, size, and whether its ends are open, pointed, or capped flat.
    
- **Key Properties & Settings:**
    
    - **Vertices (Socket - Input):** The number of vertices in the circular base. A low number creates a pyramid.
        
    - **Side Segments (Socket - Input):** The number of vertical edge loops.
        
    - **Fill Segments (Socket - Input):** The number of concentric edge loops used to fill the caps.
        
    - **Radius Top / Radius Bottom (Sockets - Input):** The radius of the top and bottom circles. Setting one to zero creates a classic pointed cone.
        
    - **Depth (Socket - Input):** The height of the cone.
        
    - **Fill Type (Property):** Determines if the top/bottom are left open ('None'), filled with a single N-gon, or filled with a fan of triangles.
        
    - **Mesh (Socket - Output):** The generated cone mesh.
        
    - **Top / Side / Bottom (Sockets - Output):** Boolean selections for the faces (or edges/vertices) of the corresponding parts of the cone, useful for assigning materials.
        
- **Practical Application:** This node is the perfect starting point for creating any kind of conical or spiky geometry on a creature, like the horns or claws of a dragon or the shell of a snail.
    
    1. **For a Horn:**
        
        - Use the Cone node. Set Radius Top to a very small number (e.g., 0.01) and Radius Bottom to a larger value (e.g., 0.2). This creates the basic tapered shape.
            
        - Set Depth to control the horn's length.
            
        - To make the horn curve, you can feed its output into a Set Position node and use a curve-shaping function (like adding a sine wave to the X-position based on the Z-position) to bend it.
            
    2. **Using the Output Selections:**
        
        - Imagine you want the base of the horn to have a rough, scaly material and the tip to be a smooth, polished material.
            
        - You can use the Top and Bottom Boolean outputs to drive a Mix node that blends between two materials or two color attributes. You can capture this mixed attribute and use it in the shader.
            
        - The Side selection can be used to assign the main horn material. This allows you to texture different parts of a single, simple primitive in a highly controlled, procedural way.