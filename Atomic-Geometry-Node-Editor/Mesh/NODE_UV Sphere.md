- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a spherical mesh using a longitude/latitude quad-based topology, with triangles meeting at the top and bottom poles.
    
- **Key Properties & Settings:**
    
    - **Segments (Socket - Input):** An integer controlling the horizontal resolution (like lines of longitude).
        
    - **Rings (Socket - Input):** An integer controlling the vertical resolution (like lines of latitude).
        
    - **Radius (Socket - Input):** The radius of the sphere.
        
    - **Mesh (Socket - Output):** The generated UV sphere mesh.
        
    - **UV Map (Socket - Output):** A default, equirectangular (world map style) UV map, ready to be stored as an attribute for texturing.
        
- **Practical Application:** The UV Sphere is the best choice when you need to use a standard rectangular texture to map onto a sphere, like creating an animal's eye.
    
    1. **The Base:** Start with a UV Sphere node. A Segments count of 32 and a Rings count of 16 usually provides enough detail.
        
    2. **The Texture:** You have a 2D image texture of an animal's iris. It's a flat, circular image on a square background.
        
    3. **The Setup:**
        
        - The UV Sphere node's UV Map output is a 2D vector. Store this on the mesh's face corners using a Store Named Attribute node (e.g., name it "eye_uv").
            
        - In the Shader Editor for the eye's material, add an Attribute node and type in "eye_uv".
            
        - Connect this attribute to the Vector input of your Image Texture node, which is loaded with your iris image.
            
    4. **The Result:** The rectangular iris texture is correctly and predictably wrapped around the sphere to create a perfect eye. The grid-like topology of the UV Sphere is specifically designed for this kind of standard texture mapping. If you tried this with an Icosphere, the texture would be distorted because its triangular, non-grid topology doesn't match the rectangular nature of the image.