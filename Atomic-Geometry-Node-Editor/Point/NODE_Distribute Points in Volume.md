- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Point
    
- **Core Function:** Generates a point cloud that fills the interior of a Volume object. The distribution of points can be random and weighted by the volume's density, or arranged in a regular grid.
    
- **Key Properties & Settings:**
    
    - **Volume (Socket - Input):** The source volume object to be filled with points.
        
    - **Distribution Method (Property):**
        
        - **Random:** Scatters points randomly. The Density input controls how many points are generated per cubic unit. The chance of a point appearing is higher in denser parts of the volume.
            
        - **Grid:** Places points in a regular, 3D grid pattern. The Spacing input controls the distance between grid points, and the Threshold input filters out points in low-density areas.
            
    - **Density (Socket - Input):** (Random mode) Controls the overall number of points.
        
    - **Spacing (Socket - Input):** (Grid mode) Controls the distance between points.
        
    - **Points (Socket - Output):** The resulting point cloud geometry.
        
- **Practical Application:** This node is perfect for creating atmospheric effects or volumetric swarms. Imagine you have a ghostly animal model that you've converted into a volume (using Mesh to Volume). You want to fill this ghost with glowing, magical motes.
    
    1. **The Goal:** To create a swarm of particles that perfectly conforms to the 3D shape of your ghost animal.
        
    2. Use the Distribute Points in Volume node. The Volume input is your ghost animal volume.
        
    3. Set the Distribution Method to 'Random'.
        
    4. You can now control the number of motes with the Density input. For a more interesting effect, you can use a Noise Texture to vary the density inside the volume before you distribute the points, which will cause the motes to naturally clump together in some areas and be sparser in others.
        
    5. The Points output is now a point cloud in the shape of your ghost. You can feed this into an Instance on Points node to place a small, glowing sphere (your "mote") at each point.
        
    6. The result is a creature made not of a solid surface, but of a cloud of thousands of individual particles, creating a beautiful and ethereal effect.