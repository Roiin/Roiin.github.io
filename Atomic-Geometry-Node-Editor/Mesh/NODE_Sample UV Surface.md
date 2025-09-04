- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Sample)
    
- **Core Function:** Performs a "reverse lookup" on a mesh's UV map. It takes a 2D UV coordinate as input, finds which face exists at that coordinate in the UV layout, and then outputs a specified attribute from that location on the 3D mesh surface. **Warning: This node requires a non-overlapping UV map to function correctly.**
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh that has the UV map you want to sample from.
        
    - **Value (Socket - Input):** The attribute on the source mesh that you want to read (e.g., Position, Normal, or a custom attribute).
        
    - **UV Map (Socket - Input):** A 2D vector field representing the UV map to use for the lookup. This is typically connected to a Named Attribute node referencing the mesh's UV map.
        
    - **Sample UV (Socket - Input):** The 2D UV coordinate(s) where you want to perform the lookup.
        
    - **Value (Socket - Output):** The primary output; the value of the sampled attribute from the location on the 3D mesh surface corresponding to the Sample UV coordinate.
        
    - **Is Valid (Socket - Output):** A Boolean that is True if a unique face was successfully found at the sample coordinate.
        
- **Practical Application:** This node is perfect for precisely placing objects on a mesh using a 2D texture as a guide, for example, placing rivets on an animal's leather armor based on a painted map.
    
    1. First, you have your animal's leather armor model with a clean, non-overlapping UV map.
        
    2. **The Prep:** In a 2D image editor, you create a black and white "rivet map" texture. You paint a white dot everywhere you want a rivet to appear.
        
    3. **The Goal:** You need to procedurally place 3D rivet models on the armor at the exact locations of these white dots.
        
    4. Create a Grid primitive. The resolution of the grid determines how accurately you will scan the texture.
        
    5. Use a Sample Texture node to read your "rivet map" using the grid's UV coordinates. Use a Compare node to select only the points where the color is white. You now have a point cloud in 2D space that matches your rivet map.
        
    6. **The Key Step:** Use the Sample UV Surface node. The Mesh is your leather armor. The Value you want to get is its Position. The UV Map is the armor's UV map. The Sample UV input comes from the positions of the points in your 2D point cloud.
        
    7. The Value output of this node is now a set of 3D positions. For every white dot on your 2D map, it has found the corresponding location on the 3D surface of the armor.
        
    8. You can now use these 3D positions to Instance on Points your rivet models, placing them with perfect precision according to your painted 2D guide.