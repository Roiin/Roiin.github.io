**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides access to the physical attributes (like density, temperature, and flame) of volumetric data from a simulation, such as a smoke or fire domain.

**Key Properties & Settings:**

- **Density (Output):** Outputs the density of the smoke simulation at any given point within the volume. This is used to define the shape and thickness of the smoke.
    
- **Flame (Output):** Outputs the density of the fire attribute of the simulation. This is typically used to control the brightness or Emission Strength of the fire.
    
- **Temperature (Output):** Outputs the temperature of the volume. This data is essential for driving the physically-based color of a fire using a Blackbody node.
    
- **Color (Output):** Outputs the color attribute baked into the volume simulation, which is useful for creating colored smoke effects.
    

**Practical Application:**  
This node is indispensable for rendering realistic fire and smoke from a physics simulation. Imagine you have simulated a fiery explosion and need to create a material for the resulting volume. A simple orange Emission shader will look like a flat, glowing blob, completely lacking realism.

The problem is that real fire's color is directly linked to its temperature: white-hot at the core, fading through yellow and orange to a dull red. The Volume Info node is the only way to feed this underlying simulation data into the shader.

1. For the volume object's material, start with a Principled Volume shader, which is designed to handle both smoke and fire.
    
2. Connect the Density output from the Volume Info node directly to the Density input of the Principled Volume shader. This immediately gives the smoke its simulated shape.
    
3. To create the fire, connect the Temperature output to a Math node set to Multiply. Simulation temperatures are often low, so multiply them by a large value (e.g., 2500) to bring them into a realistic Kelvin range.
    
4. Feed the result of the Math node into a Blackbody node. This will convert the raw temperature data into physically accurate fire colors.
    
5. Connect the Blackbody node's output to the Emission Color input of the Principled Volume shader. The volume will now glow with a realistic temperature-based gradient, creating a convincing fire effect that is directly driven by the physics simulation.