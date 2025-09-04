**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides different coordinate systems that dictate how textures are mapped onto an object's surface.

**Key Properties & Settings:**

- **UV (Output):** The most crucial output for precise texture mapping. It uses the object's artist-created UV map to place textures, offering complete control over placement, orientation, and scale. This is the standard for applying image textures.
    
- **Generated (Output):** The default coordinate system used by most procedural textures. It automatically projects the texture based on the object's initial bounding box, making it quick and easy for procedural effects that don't require precise alignment.
    
- **Object (Output):** Uses another object's (often an Empty) coordinate space to project a texture. This is excellent for preventing texture "swimming" on deforming objects or for projecting a texture onto multiple objects at once.
    
- **Window (Output):** Maps the texture directly to the 2D space of the final rendered image, as if the texture were a sticker on the camera lens.
    
- **From Instancer [Cycles Only]:** When an object is instanced (e.g., via a particle system), this option forces the instance to inherit the texture coordinates from the parent instancer object.
    

**Practical Application:**  
This node is the starting point for almost any texturing task. Consider creating a material for a wooden table. You have a seamless image texture of **wood grain** that needs to be applied to the tabletop.

The problem is that if you plug the Image Texture node directly into your shader, Blender uses Generated coordinates by default. On a rectangular tabletop, this will stretch the square image texture to fit the rectangular bounding box, resulting in a distorted, unrealistic grain. You need the grain to flow naturally along the length of the table. The Texture Coordinate node is the solution.

1. First, you must create a UV map for your table object in the UV Editing workspace, a process called "unwrapping." For the tabletop, you would unwrap it into a clean rectangle that matches its proportions.
    
2. In the Shader Editor, add a Texture Coordinate node.
    
3. Connect the UV output socket to the Vector input of your Image Texture node.
    
4. This action explicitly tells Blender to stop guessing with Generated coordinates and instead use your carefully prepared UV map. The wood grain texture will now be mapped perfectly to the tabletop's surface, following the direction you defined in the UV map and eliminating any unwanted stretching. This is the fundamental workflow for applying any image-based texture with precision.