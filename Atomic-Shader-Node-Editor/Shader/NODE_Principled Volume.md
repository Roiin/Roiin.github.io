**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** An all-in-one, physically-based shader for creating volumetric effects like smoke, fire, and fog by combining scattering, absorption, and emission properties into a single node.

**Key Properties & Settings:**

- **Density Controls:**
    
    - **Density:** A multiplier for the volume's thickness. Higher values create denser, more opaque smoke.
        
    - **Density Attribute:** A text field where you enter the name of the voxel data grid (e.g., "density") from a simulation to define the volume's shape.
        
- **Color & Scattering:**
    
    - **Color:** The scatter color of the volume. This is the color of the smoke when it is lit by an external light source.
        
    - **Absorption Color:** The color the volume absorbs as light passes through it. This effectively tints the volume, especially in its denser areas.
        
    - **Anisotropy:** Controls the direction of light scattering. Positive values cause light to scatter forward (like steam), making the volume appear brighter when backlit.
        
- **Fire & Emission Controls:**
    
    - **Temperature:** Drives the heat of the volume, which is used for physically-based Blackbody emission.
        
    - **Temperature Attribute:** A text field for the name of the temperature grid from a simulation (e.g., "flame" or "temperature").
        
    - **Blackbody Intensity:** A multiplier for the physically-accurate light emission based on the Temperature input. A value of 1.0 is physically correct.
        
    - **Emission Strength / Color:** A simpler, non-physical emission for creating uniform glows that are not dependent on temperature.
        
- **Volume (Output):** The shader's only output. It must be connected to the Volume input of a Material Output or World Output node.
    

**Practical Application:**  
This node is the standard tool for rendering the results of a fluid simulation, such as fire and smoke. Imagine you've created a simulation of a campfire. You have the raw voxel data, but you need to make it look like a real fire, with dense smoke and a glowing, temperature-driven flame.

The problem is that the raw simulation data contains no visual information, only physical properties like density and temperature. You need a shader that can interpret this data and render it. The Principled Volume shader is built for this exact purpose.

1. Apply a new material to your smoke domain object and connect a Principled Volume shader to the Volume input of the Material Output node (do not use the Surface input).
    
2. To give the smoke its shape, type the name of the density grid from your simulation (typically "density") into the Density Attribute text box.
    
3. To create the fire, type the name of the temperature grid (e.g., "temperature" or "flame") into the Temperature Attribute text box.
    
4. Set the Blackbody Intensity to 1.0. The shader will now automatically read the temperature data for each point in the volume and convert it into a physically-accurate fire color and brightness—hotter areas will be brighter and whiter, while cooler areas will be a duller red.
    
5. Finally, set the Color input to a dark gray to give the smoke its sooty appearance. The node successfully translates the abstract simulation data into a realistic visual of smoke and fire.