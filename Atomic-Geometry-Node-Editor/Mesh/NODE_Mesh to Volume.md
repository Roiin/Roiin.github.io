- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Converts a closed, manifold mesh into a volumetric object, creating a fog-like volume that fills the interior of the mesh shape.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be converted. For best results, this mesh should be manifold (watertight, with no holes).
        
    - **Density (Socket - Input):** A float value that controls the density of the generated volume. Higher values create a thicker, more opaque fog.
        
    - **Resolution Mode (Property):**
        
        - **Voxel Size:** Defines the size of each individual 3D pixel (voxel). Smaller values create a higher-resolution, more detailed volume but are much slower to process.
            
        - **Voxel Amount:** Defines the resolution by the approximate number of voxels along the longest axis of the mesh's bounding box.
            
    - **Interior Band Width (Socket - Input):** Creates a hollow volume by generating density only within a certain distance of the mesh's inner surface, rather than filling the entire interior.
        
    - **Volume (Socket - Output):** The resulting volume object, ready to be rendered with a volumetric shader.
        
- **Practical Application:** This node is perfect for creating stylized, volumetric effects shaped like creatures, for example, a ghost animal.
    
    1. Start with a standard 3D model of an animal, like a wolf.
        
    2. **The Goal:** You want to transform this solid model into a semi-transparent, ethereal ghost made of swirling fog.
        
    3. Use the Mesh to Volume node on the wolf mesh. This creates a volume object perfectly in the shape of the wolf.
        
    4. To make the fog look more natural and less uniform, you can use a Noise Texture to drive the Density input. This will create variations in the fog's thickness, with some parts being denser and others more wispy.
        
    5. To make the ghost's edges fade out softly, you can use the Interior Band Width parameter to make the volume hollow, or use a Geometry Proximity node to decrease the density near the surface.
        
    6. The final Volume output can be assigned a material with a Principled Volume shader. By giving it a slight emission color, you can create a glowing, spectral wolf that has a tangible, volumetric presence in the scene.