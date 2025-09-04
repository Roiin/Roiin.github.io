**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Loads and maps an external image file (like a JPG, PNG, or EXR) onto a surface to be used as a texture.

**Key Properties & Settings:**

- **Color (Output):** The primary output, providing the RGB color data from the image.
    
- **Alpha (Output):** Provides the grayscale alpha (transparency) channel from the image, if one exists.
    
- **Image (Property):** The data block where you load your image file.
    
- **Vector (Input):** The crucial input that defines the texture mapping. This is almost always connected to a Texture Coordinate node, most commonly using the UV output for precise, artist-controlled mapping.
    
- **Projection (Property):** Determines how the texture is wrapped if not using a UV map. Flat is the default for UVs. Box is useful for quickly texturing architectural shapes without UV unwrapping.
    
- **Extension (Property):** Controls what happens when the texture coordinates go beyond the image's boundaries. Repeat (the default) tiles the image, which is perfect for seamless textures. Clip makes the area outside the image transparent.
    
- **Color Space (Property):** Specifies how Blender should interpret the color data in the file. For standard color images (JPG, PNG), this should be sRGB. For data maps like normal maps or roughness maps, it must be set to Non-Color.
    

**Practical Application:**  
This node is the cornerstone of texturing work, used whenever you need to apply a pre-made image to a model. It is the definitive way to apply a **wood grain** texture to a piece of furniture.

The problem is that a procedural wood grain can be complex to create and difficult to art direct. Using a high-quality photo of real wood is often faster and more realistic. The Image Texture node is the solution for applying that photo.

1. Start with a Principled BSDF.
    
2. Add an Image Texture node and open your seamless wood grain image file.
    
3. Because this image contains color information, ensure its Color Space is set to sRGB.
    
4. Connect the Color output of the Image Texture node to the Base Color input of the Principled BSDF.
    
5. To map the texture correctly, add a Texture Coordinate node and connect its UV output to the Vector input of the Image Texture node. This tells Blender to use your object's UV map for precise placement.
    
6. The result is that your photographic wood grain texture is now perfectly applied to the surface of your model, following the layout you defined in your UV map. This same workflow applies to roughness maps, metallic maps, and normal maps, where you would load the appropriate grayscale image and set its Color Space to Non-Color.