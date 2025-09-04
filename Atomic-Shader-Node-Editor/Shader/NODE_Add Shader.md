**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Combines two shaders by literally adding their light interactions together, resulting in a brighter, non-physical material that layers the effects.

**Key Properties & Settings:**

- **Shader (Input):** Two green shader sockets where you plug in the shaders you want to combine.
    
- **Shader (Output):** The final, combined shader result. The output will be at least as bright as the brightest of the two inputs, as their light contributions are summed.
    

**Practical Application:**  
This node is excellent for creating effects where one material needs to be layered on top of another without blending, such as adding a clear coat or emissive details. Consider creating **molten lava** with a cooling, dark crust and glowing cracks.

The problem is that if you use a Mix Shader, the glowing lava would replace the dark crust in the cracks. You need the dark crust to remain solid while having the glow appear on top of it. The Add Shader is the solution for this layering.

1. Create your base shader for the dark, cooling rock crust (e.g., a Principled BSDF with a dark color and high roughness).
    
2. Create your glowing lava shader using an Emission shader. Use a Noise Texture plugged into the Strength input to make the emission appear only in a crack-like pattern.
    
3. Connect the dark crust shader to the top input of an Add Shader node and the lava Emission shader to the bottom input.
    
4. The result is a material where the dark crust is fully opaque and visible, and the light from the Emission shader is additively layered on top. This creates the convincing effect of light emanating from within the cracks, a look that would be difficult to achieve with a standard Mix Shader.