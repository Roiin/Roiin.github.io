**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Allows a material to change its appearance based on the type of light ray interacting with it, enabling non-physical effects and optimizations.

**Key Properties & Settings:**

- **Is Camera Ray:** The most common output. It is 1.0 (white) only for rays that travel directly from the surface to the camera. This allows you to create one appearance for the camera and a different one for reflections, shadows, and global illumination.
    
- **Is Shadow Ray:** Becomes 1.0 when Blender is calculating shadows cast by the object. It can be used to make an object cast a colored shadow or no shadow at all.
    
- **Is Reflection Ray [Cycles Only]:** Becomes 1.0 for rays seen in reflective surfaces. Useful for creating a simplified version of a material that is only seen in reflections to speed up render times.
    
- **Is Transmission Ray [Cycles Only]:** Becomes 1.0 for rays seen through refractive/transmissive surfaces like glass or water.
    
- **Ray Depth:** Outputs the number of times a ray has bounced. This can be used to change or simplify a material after a certain number of reflections to prevent "black mirror" artifacts and reduce render time.
    

**Practical Application:**  
This node is the key to creating materials that are visually complex but computationally simple. Consider creating a **molten lava** flow. The lava needs to look detailed to the camera, with a dark, cooling crust and bright cracks, but it must also cast a powerful, uniform orange light to illuminate the surrounding environment.

The problem is that if you use a texture to create the dark crust on an Emission shader, those dark parts won't emit light, killing the global illumination effect. But if you turn the emission strength up high enough to cast light, the texture detail will be completely washed out and white to the camera. The Light Path node is the solution.

1. Create two separate shader paths. The first is a complex Principled BSDF with noise textures to create the detailed "camera view" of the crust and glowing cracks. The second is a simple, high-strength orange Emission shader for "global illumination".
    
2. Add a Mix Shader node.
    
3. Connect the Is Camera Ray output of the Light Path node to the Fac input of the Mix Shader.
    
4. Plug the complex "camera view" shader into the bottom socket of the Mix Shader, and the simple Emission shader into the top socket.
    
5. This setup tells the material: "If the camera is looking directly at you, show the detailed crust. For every other purpose (calculating light bounces, reflections, etc.), just pretend you are a simple, bright light source." This gives you the best of both worlds: a visually interesting surface and realistic, efficient global illumination.