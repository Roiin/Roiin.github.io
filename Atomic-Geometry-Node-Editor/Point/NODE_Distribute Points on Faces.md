- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Point
    
- **Core Function:** Scatters points across the surface of a mesh. This is the primary node for populating surfaces with instances like trees, rocks, scales, or fur. It provides methods for both random and more structured, evenly spaced distributions.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh whose faces will be used for scattering.
        
    - **Selection (Socket - Input):** A Boolean face selection. Points will only be generated on selected faces.
        
    - **Distribution Method (Property):**
        
        - **Random:** Scatters points completely randomly. The Density input controls the number of points per square meter.
            
        - **Poisson Disk:** Scatters points randomly but enforces a minimum distance between them, preventing points from clumping too closely. This creates a more natural, "blue noise" distribution. The Distance Min input controls this spacing.
            
    - **Density (Socket - Input):** A float field that controls the density of the scattered points. This can be driven by a texture or attribute to create areas with more or fewer points.
        
    - **Seed (Socket - Input):** An integer to change the random pattern.
        
    - **Points (Socket - Output):** The resulting point cloud.
        
    - **Normal (Socket - Output):** The normal vector of the face underneath each generated point. This is crucial for aligning instances to the surface.
        
    - **Rotation (Socket - Output):-** A pre-calculated XYZ Euler rotation aligned to the surface normal, ready for use with instancing nodes.
        
- **Practical Application:** This node is the foundation for adding surface details to a creature, such as the scales on a lizard.
    
    1. Start with your lizard model.
        
    2. **The Goal:** To cover the lizard's skin with thousands of individual scale instances.
        
    3. Use the Distribute Points on Faces node.
        
        - Set the Distribution Method to 'Poisson Disk'. This is critical for scales, as it ensures they don't overlap and maintain a somewhat regular spacing, which looks much more natural than pure random.
            
        - Set the Distance Min to a value that is slightly larger than the radius of your scale model. This guarantees the scales won't intersect.
            
        - Use the Density input to control the overall number of scales. You could even use a texture to make the scales denser in some areas (like the back) and sparser in others (like the belly).
            
    4. Feed the Points output into an Instance on Points node. For the Instance, use your scale model.
        
    5. Connect the Rotation output directly to the Rotation input of the Instance on Points node. This will automatically align every single scale to be flush with the curved surface of the lizard's body.
        
    6. The result is a perfectly scaled creature, generated procedurally. You can easily change the size, density, and spacing of the scales just by adjusting a few parameters.