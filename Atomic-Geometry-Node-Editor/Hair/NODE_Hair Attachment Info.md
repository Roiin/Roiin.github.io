**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Read)

**Core Function:** Retrieves information about how and where hair curves are attached to a specific surface mesh, primarily their UV coordinates.

**Key Properties & Settings:**

- **Surface Geometry (Input):** The mesh geometry to which the hair is attached.
    
- **Surface UV Map (Input):** The specific UV map on the surface mesh that should be referenced.
    
- **Attachment UV (Output):** The 2D UV coordinate on the surface mesh that corresponds to the root of each hair curve.
    
- **Attachment is Valid (Output):** A boolean that is True if a hair curve has a valid attachment on the specified surface and UV map.
    
- **Surface Normal (Output):** The normal vector of the surface mesh at the exact point of each hair's attachment.
    

**Practical Application:**  
This node is crucial for transferring surface data, like color from a texture map, onto the hair curves themselves. Imagine you are creating the fur for a zebra, and you need the hair to be black or white based on an underlying stripe pattern texture.

- **The Goal:** To set the color of each hair curve based on the color of the zebra's skin texture directly beneath its root.
    
- **The Problem:** The hair curves are a separate geometry from the zebra's skin mesh. By default, they have no knowledge of the skin's UVs or its material. You need a way to "sample" the skin texture at the root of each hair.
    
- **The Solution:** The Hair Attachment Info node provides the necessary UV coordinates to perform this sampling.
    
    1. Place the Hair Attachment Info node in your tree. Connect the zebra's mesh geometry to the Surface Geometry input and specify its main UV map.
        
    2. The Attachment UV output now provides the correct 2D UV coordinate for each hair's root.
        
    3. Use an Image Texture node and load your zebra's black-and-white stripe pattern.
        
    4. Connect the Attachment UV output directly into the Vector (UV) input of the Image Texture node.
        
    5. The Color output of the Image Texture node will now be a field of colors, where each hair has the color sampled from the skin at its root.
        
    6. You can now use this color data to drive a Set Material Index node (e.g., if color is black, use material 1; if white, use material 2) or store it as an attribute to be used directly in a shader.
        

This creates a perfect correspondence between the skin pattern and the fur color, ensuring the zebra's stripes are accurately rendered in the final groom.