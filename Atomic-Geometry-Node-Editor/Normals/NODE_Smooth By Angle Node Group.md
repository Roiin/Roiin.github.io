**Editor:** Geometry Nodes Editor  
**Node Group:** Normals Nodes

>[!NOTE]
> This is a pre-made node group that is included with Blender's "Essentials" asset library.

**Core Function:** Automatically sets the sharpness of mesh edges based on the angle between their adjacent faces, allowing for procedural control over smooth and hard-surface shading.

**Key Properties & Settings:**

- **Mesh (Input):** The mesh geometry whose edges will be processed.
    
- **Angle (Input):** The threshold angle, in degrees. Edges where the angle between neighboring faces is less than this value will be marked as "smooth." Edges where the angle is greater will be marked as "sharp."
    
- **Ignore Sharpness (Input):** A boolean that, when True, forces all edges to be smooth, overriding the angle calculation.
    

**Practical Application:**  
This node is essential for correctly shading models that have both rounded and sharp features, without needing to manually mark every edge. Imagine you have a procedural model of a rhinoceros.

- **The Goal:** To make the rhino's horn and ears appear sharp and well-defined, while its main body looks smooth and organic, all automatically.
    
- **The Problem:** By default, a mesh is either rendered as entirely smooth-shaded (which would make the horn look like a soft blob) or entirely flat-shaded (which would make the body look faceted and low-poly). Manually setting the sharpness for every edge on a procedural model is impossible.
    
- **The Solution:** The Smooth By Angle node automates this distinction.
    
    1. Place the Smooth By Angle node group after your final rhino geometry has been generated.
        
    2. Set the Angle to a value like 45 degrees.
        
    3. The node will now analyze every edge of the rhino model.
        
        - On the rhino's rounded body, the angle between any two adjacent faces is very small (less than 45°), so those edges will be set to smooth.
            
        - At the sharp base of the horn or the crisp edges of the ears, the angle between faces is very large (much greater than 45°), so those edges will be set to sharp.
            
    4. The Mesh output now has the correct sharpness data. When rendered, the rhino will have a perfectly smooth body and a crisply defined horn, achieving a professional look with a single, simple control.