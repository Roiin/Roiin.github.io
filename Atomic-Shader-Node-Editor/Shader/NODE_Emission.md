**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Creates a material that emits light from its surface, turning the object itself into a light source.

**Key Properties & Settings:**

- **Emission (Output):** The standard shader output. This can be connected to the Surface or Volume input of the Material Output node.
    
- **Color (Input):** Defines the hue and saturation of the light being emitted.
    
- **Strength (Input):** Controls the intensity of the emitted light. A value of 1.0 creates a "shadeless" material that appears uniformly lit with the exact input Color, unaffected by scene lighting. Values greater than 1.0 will cause the surface to cast light and contribute to the scene's global illumination.
    

**Practical Application:**  
This node is essential for any material that needs to glow or appear self-illuminated. It is the core component for creating materials like neon signs, light sabers, or the glowing cracks in **molten lava**.

The problem with creating lava is that a simple orange texture on a rock shader looks like cold, painted rock. It lacks the intense heat and energy of real lava. You need the material to actively cast light. The Emission shader is the solution.

1. Start by creating a base Principled BSDF for the dark, cooling crust of the lava flow.
    
2. Use a Noise Texture, crunched through a ColorRamp to create a high-contrast black and white "crack" pattern. This will be your mask.
    
3. Create an Emission shader and set its Color to a fiery orange or yellow. Set the Strength to a high value (e.g., 20 or more) to make it cast a powerful glow.
    
4. Use a Mix Shader node to combine the dark crust shader (top input) and the Emission shader (bottom input). Plug the "crack" mask into the Fac input.
    
5. The result is a convincing lava material. The dark crust appears solid, while the areas defined by the mask glow intensely, casting orange light onto nearby objects and contributing to the scene's overall lighting, perfectly simulating a surface that is white-hot with heat.