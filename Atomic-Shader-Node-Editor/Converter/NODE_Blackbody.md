**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Converts a temperature value (in Kelvin) into a physically-based, corresponding color, simulating the color of an object heated to that temperature.

**Key Properties & Settings:**

- **Color (Output):** The primary output, providing the final RGB color that corresponds to the input temperature.
    
- **Temperature (Input):** The sole input. It accepts a value representing a temperature in Kelvin. The node translates this value along the blackbody radiation spectrum: low temperatures are red, progressing to yellow, then white-hot, and eventually to a light blue at extremely high temperatures.
    

**Practical Application:**  
This node is essential for creating physically accurate emissive materials where color is determined by heat, such as fire, star filaments, or **molten lava**.

The problem with creating lava is that a simple orange Emission shader looks flat and unrealistic. Real lava has a temperature gradient—it's white-hot at its core and cools to a deep red at the edges. You need the color to be directly driven by this temperature variation. The Blackbody node is the solution.

1. Create a procedural heat map for your lava using a Noise Texture. The white areas of the noise will represent the hottest parts, and the black areas will be the coolest.
    
2. The noise texture's 0-to-1 output needs to be scaled to a realistic temperature range. Use a Map Range node to convert the 0-to-1 input range to an output range of approximately 1200 to 2500 Kelvin, which is a plausible range for lava.
    
3. Connect the output of the Map Range node directly into the Temperature input of the Blackbody node.
    
4. Connect the Color output of the Blackbody node to the Emission Color input of your Principled BSDF. You can also use the heat map to drive the Emission Strength.
    
5. The result is a highly realistic lava material. The color is no longer a single, flat orange. Instead, it has a physically-based gradient where the hottest areas are a brilliant white-yellow, and the cooler areas are a deep, glowing red, all driven by the underlying procedural temperature data.