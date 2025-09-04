- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Volume (Primitives)
    
- **Core Function:** Generates a new, rectangular volume "from scratch". It creates a 3D grid of voxels and evaluates a Density field at the position of each voxel to determine its value. This is the primary method for creating volumes based on procedural textures and mathematical formulas.
    
- **Key Properties & Settings:**
    
    - **Density (Socket - Input):** The critical input. A float field that defines the density at any given point in space. This is typically driven by a Noise Texture or other math nodes that use the Position node as an input.
        
    - **Min / Max (Sockets - Input):** Two vector inputs that define the opposite corners of the bounding box for the volume.
        
    - **Resolution X, Y, Z (Sockets - Input):** Integers that control the number of voxels along each axis, determining the volume's level of detail. Be cautious, as performance decreases cubically with higher resolution.
        
    - **Background (Socket - Input):** The density value for the space outside the bounding box.
        
    - **Volume (Socket - Output):** The generated volume object.
        
- **Practical Application:** This node is the ideal tool for creating procedural clouds or nebula effects, without needing any input mesh.
    
    1. **The Goal:** To create a single, puffy, stylized cloud.
        
    2. Use the Volume Cube node. Set the Min and Max inputs to define the overall size of the cloud (e.g., Min: [-2,-2,-1], Max: [2,2,1]).
        
    3. **The Shape:** By default, the volume is a uniform block. To make it look like a cloud, you need to vary its Density.
        
        - Connect a Noise Texture to the Density input. Use the Position node as the vector input for the texture.
            
        - To shape the noise into a cloud, use a Color Ramp node after the Noise Texture. By adjusting the color ramp's handles, you can increase the contrast, creating sharp, well-defined "puffs" of density and large areas of empty space (zero density).
            
        - To make the cloud fade out at the edges of its box, you can create a spherical gradient (using the Vector Math 'Distance' from the center) and multiply it with your noise density.
            
    4. **The Result:** A fully procedural, three-dimensional cloud contained within the bounding box. You can easily change its shape by altering the Noise Texture settings, or create a whole sky full of unique clouds by instancing this setup and giving each instance a different Seed.