**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Selects and outputs the coordinates from a specific UV map by its name, allowing a single material to access multiple, different UV layouts on the same object.

**Key Properties & Settings:**

- **UV (Output):** The primary output, providing the vector coordinates for the specified UV map. This should be connected to the Vector input of a texture node.
    
- **UV Map (Property):** A dropdown menu that lists all available UV maps on the object. This is the node's core control, allowing you to explicitly choose which coordinate set to use.
    
- **From Instancer [Cycles Only]:** When used on an instanced object, this will attempt to use the UV map from the instancer object instead of the instance itself.
    

**Practical Application:**  
This node is an advanced tool for complex texturing where one coordinate system isn't enough. Imagine creating a material for a detailed video game asset, like a sci-fi weapon. You need a high-resolution, non-overlapping UV map for the main painted details and decals. However, you also want to overlay a seamless, tiled texture for surface details like a fine carbon-fiber pattern or generic **rust**.

The problem is that a single UV map can't do both jobs well. The custom-unwrapped map for the decals would cause a tiled texture to have visible seams, and a simple, repeating UV map (like a Cube Projection) would distort the decals. You need two different mapping strategies on one material. The UV Map node is the solution.

1. On your mesh, create two separate UV maps. Name the first one "UV_Decals" and carefully unwrap the object to place your decals without distortion. Name the second one "UV_Tiling" and create it using a simple Cube Projection unwrap, which is ideal for seamless textures.
    
2. In the Shader Editor, use the standard Texture Coordinate node. Its UV output will use the currently active render map (let's say "UV_Decals") to drive your main decal Image Texture.
    
3. Now, add a UV Map node. From its dropdown menu, explicitly select "UV_Tiling".
    
4. Connect the output of this UV Map node to the Vector input of your seamless rust or carbon-fiber Image Texture.
    
5. Finally, use a Mix Color node to blend the decal texture and the tiling texture together. This allows you to combine the precision of a hand-made UV layout with the efficiency of a generic, seamlessly tiled overlay within a single material.