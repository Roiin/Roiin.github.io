- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Write)
    
- **Core Function:** Allows for the procedural setting of custom normals on a mesh, overriding the automatically calculated ones. This provides precise control over how a surface is shaded, allowing for effects like smoothing faceted surfaces or creating artificial hard edges without altering the geometry.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The mesh geometry whose normals will be modified.
        
    - **Mode (Property):** The method for setting normals:
        
        - **Sharpness:** The simplest mode. Allows you to set edges as 'Sharp' or faces as 'Flat' based on a Boolean input, similar to Edit Mode tools.
            
        - **Free:** The most direct mode. You provide a vector field to the Custom Normal input, and this vector is used as the new normal. It's fast but doesn't work well with deforming meshes.
            
        - **Tangent Space:** A more advanced mode for deforming meshes.
            
    - **Custom Normal (Socket - Input):** In 'Free' mode, this vector input provides the new normal directions.
        
- **Practical Application:** The 'Free' mode is incredibly powerful for faking high-detail geometry on a low-poly model, a common technique in game development. Imagine you have a very simple, low-poly model of a tree trunk, and a separate, highly detailed, sculpted version.
    
    1. **The Goal:** You want the low-poly trunk to have the smooth, detailed shading of the high-poly sculpt without the performance cost.
        
    2. **The Prep:** First, you "bake" a Normal Map texture from the high-poly model to the low-poly model. This texture stores the detailed surface normals of the sculpt as colors.
        
    3. **The Node Tree:**
        
        - Use a Sample Texture node to read the Normal Map texture. The output is a color vector that represents the desired normal directions.
            
        - Because Normal Maps are stored in "tangent space," you will need to convert this vector into world space. This often involves a few vector math nodes using the mesh's original Normal and Tangent.
            
        - Use the Set Mesh Normal node in Free mode.
            
        - Feed the final, converted normal vector from your texture into the Custom Normal input.
            
    4. **The Result:** The low-poly, faceted tree trunk will now render with the illusion of having all the smooth curves, bumps, and details of the high-poly sculpt. Its shading will be incredibly rich and detailed, even though its underlying geometry is still very simple. This node is the key to applying baked normal map data procedurally.