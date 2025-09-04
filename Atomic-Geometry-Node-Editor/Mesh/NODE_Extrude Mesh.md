- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Extrudes selected mesh elements (vertices, edges, or faces) outwards, creating new geometry in the process. Unlike simple translation, extrusion duplicates the selected elements and generates connecting "side" geometry.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be extruded.
        
    - **Selection (Socket - Input):** A Boolean mask. Only selected elements will be extruded.
        
    - **Offset (Socket - Input):** A vector defining the direction and distance of the extrusion. By default, it uses the element's normal, which is the most common use case.
        
    - **Offset Scale (Socket - Input):** A float that multiplies the Offset vector, allowing for easy control over the extrusion height.
        
    - **Individual (Socket - Input):** In 'Face' mode, a Boolean that controls whether connected faces are extruded as a single group (False) or if each face is extruded on its own, creating gaps between them (True).
        
    - **Mode (Property):** The type of element to extrude: Vertices, Edges, or Faces.
        
    - **Top (Socket - Output):** A Boolean selection for the newly created "cap" of the extrusion.
        
    - **Side (Socket - Output):** A Boolean selection for the newly created connecting geometry "walls" of the extrusion.
        
- **Practical Application:** This node is essential for adding 3D volume to flat shapes, such as creating the buildings of a city from a 2D floor plan.
    
    1. Start with a 2D mesh of building footprints. This could be a Grid or a more complex shape.
        
    2. **The Goal:** You want to extrude these flat footprints upwards to create buildings of varying heights.
        
    3. Use the Extrude Mesh node with the Mode set to 'Faces'.
        
    4. To create varied heights, you need a random Offset Scale for each building. If each footprint is a separate Mesh Island, you can use the Island Index as the Seed for a Random Value node to generate a unique height for each building.
        
    5. The Top and Side outputs are invaluable for texturing. You can use them with a Set Material node:
        
        - Use the Top selection to assign a "Rooftop" material.
            
        - Use the Side selection to assign a "Brick Wall" material with windows.
            
    6. The result is a procedurally generated city block. The Extrude Mesh node created the 3D form, the random height variation made it look more natural, and the Top/Side outputs allowed for intelligent, automatic material assignment.