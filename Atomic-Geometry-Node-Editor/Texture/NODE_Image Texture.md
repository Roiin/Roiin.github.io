- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Samples an external image file at a given coordinate and outputs the color and alpha information. This is the main tool for using textures to control displacement, density, scale, and other attributes.
    
- **Key Properties & Settings:**
    
    - **Image (Data-Block):** A selector on the node to load or choose the image file to be used.
        
    - **Vector (Socket - Input):** The 2D coordinate at which to sample the image. This is almost always connected to a UV map attribute. If left unconnected, it will attempt to use the 3D Position, which is usually not desired.
        
    - **Frame (Socket - Input):** For image sequences or video files, this float input determines which frame of the animation to sample.
        
    - **Interpolation (Property):** Controls how the texture is sampled between pixels ('Linear' for soft, 'Closest' for pixelated).
        
    - **Extension (Property):** Controls how the texture behaves outside the 0-1 UV space ('Repeat' for tiling, 'Clip' to stop, etc.).
        
    - **Color (Socket - Output):** The RGBA color value from the image at the sample coordinate.
        
    - **Alpha (Socket - Output):** The alpha (transparency) value from the image at the sample coordinate.
        
- **Practical Application:** This node is perfect for using a hand-painted map to control the placement of details on a creature, like adding a patch of unique, bioluminescent scales to a deep-sea animal.
    
    1. First, you have your sea creature model with a proper, non-overlapping UV map.
        
    2. **The Prep:** In a 2D image editor, you paint a texture. Most of it is black, but you paint a white, feathered patch on the part of the UV map corresponding to the creature's back. This is your "glow map".
        
    3. **The Goal:** You want to scatter glowing scale instances only on the white parts of the glow map.
        
    4. Use the Image Texture node and load your glow map.
        
    5. For the Vector input, use a Named Attribute node to get your creature's UV map (e.g., "UVMap").
        
    6. The Color or Alpha output of the texture node is now a field on your mesh's surface that corresponds to your painted map.
        
    7. This field is a perfect density mask. Feed it into the Density input of a Distribute Points on Faces node.
        
    8. **The Result:** Points (and thus, your instanced glowing scales) will only be generated on the parts of the mesh where you painted white. The feathered edges of your brush stroke will translate into a natural falloff in the density of the scales. This gives an artist precise, pixel-level control over a procedural effect.