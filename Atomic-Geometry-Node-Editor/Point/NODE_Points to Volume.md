- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Point
    
- **Core Function:** For each point in a point cloud, this node generates a spherical volume of fog around it. When these spherical volumes overlap, their densities are added together, creating a single, cohesive, cloud-like volume.
    
- **Key Properties & Settings:**
    
    - **Points (Socket - Input):** The source point cloud.
        
    - **Radius (Socket - Input):** A float field that controls the size of the spherical volume generated at each point.
        
    - **Density (Socket - Input):** A float field that controls the density of the volume generated at each point.
        
    - **Resolution Mode (Property):**
        
        - **Voxel Size:** Defines the size of each 3D pixel (voxel), controlling the final resolution of the volume.
            
        - **Voxel Amount:** Defines the resolution by the number of voxels along the longest axis.
            
    - **Volume (Socket - Output):** The resulting volume object.
        
- **Practical Application:** This node is perfect for creating organic, blobby creatures or cloud-like animals.
    
    1. **The Goal:** To create a stylized, puffy cloud in the shape of a sheep.
        
    2. **The Base:** Start with a very simple, low-poly mesh of a sheep's body. Use a Distribute Points on Faces or Distribute Points in Volume node to fill this shape with a cloud of points.
        
    3. Use the Points to Volume node on this point cloud.
        
        - The Radius input is key. By giving it a large enough value, the individual spheres of fog around each point will overlap and blend together smoothly. You can use a Noise Texture to vary the radius for a more lumpy, natural look.
            
        - The Voxel Size determines the final quality. A smaller size will create a smoother, more detailed cloud but will be much slower.
            
    4. The output is a single volume object that has the overall shape of a sheep but with a soft, cloud-like appearance.
        
    5. You can then take this one step further by feeding this volume into a Volume to Mesh node, which will generate a single, smooth, "metaball"-style mesh that looks like a sculpted cloud.