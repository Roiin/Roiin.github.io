- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a spherical mesh composed of evenly distributed triangles (an icosahedron), which avoids the pinching and poles found on a standard UV Sphere.
    
- **Key Properties & Settings:**
    
    - **Radius (Socket - Input):** The radius of the sphere.
        
    - **Subdivisions (Socket - Input):** An integer controlling the resolution. Each level of subdivision splits every triangle into four smaller ones, rapidly increasing the density.
        
    - **Mesh (Socket - Output):** The generated icosphere mesh.
        
    - **UV Map (Socket - Output):** A default UV map for the icosphere.
        
- **Practical Application:** The Icosphere is the ideal base for procedural planets, asteroids, or stylized, "bumpy" creatures because its faces are all roughly the same size and shape, leading to more uniform displacement.
    
    1. **The Goal:** To create a procedurally generated asteroid or a lumpy cartoon animal.
        
    2. **The Base:** Start with an Icosphere node. A Subdivisions level of 4 or 5 provides a good amount of detail to work with.
        
    3. **The Displacement:** Use a Set Position node. For the Offset, you'll use noise.
        
    4. Connect a Noise Texture node to a Vector Math 'Scale' node.
        
    5. For the other input of the 'Scale' node, use the Normal of the icosphere. This ensures the displacement happens outwards from the center, maintaining the spherical shape.
        
    6. Connect the result to the Offset of the Set Position node. You can control the "bumpiness" by adjusting the scale of the noise texture and the scale factor in the Vector Math node.
        
    7. **The Result:** Because the icosphere's triangles are all evenly sized, the displacement from the noise texture is applied uniformly across the entire surface. This avoids the stretching and distortion artifacts you would see if you applied the same effect to a UV Sphere, where the faces get pinched and tiny near the poles.