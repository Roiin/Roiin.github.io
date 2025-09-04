**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Converts a specific wavelength of light (in nanometers) into its corresponding, pure spectral color.

**Key Properties & Settings:**

- **Color (Output):** The primary output, providing the pure RGB color that represents the input wavelength.
    
- **Wavelength (Input):** The sole input. It accepts a value representing a wavelength in nanometers, typically within the visible spectrum (approximately 380nm to 780nm).
    

**Practical Application:**  
This node is a specialized tool for scientific visualization and for creating physically-based optical effects like dispersion, where light splits into a rainbow. It is the perfect node for simulating a prism or the "fire" in a diamond.

The problem with creating a rainbow effect is that you cannot simply use a rainbow-colored image texture, because the colors need to be physically accurate and correspond to the refractive index of the material. Different wavelengths of light bend at slightly different angles. The Wavelength node is the solution for generating these pure spectral colors.

1. A physically-based dispersion shader is complex, but the core principle relies on rendering the scene three times (or using three shaders), one for each primary color, with a slightly different Index of Refraction (IOR) for each.
    
2. Add a Separate XYZ node to a Geometry node's Incoming vector.
    
3. For the "Red" component of your shader, you would use a Wavelength node with the Wavelength set to a red value (e.g., 650nm). You would then build a Glass BSDF whose IOR is calculated for this red wavelength.
    
4. You would repeat this for a "Green" shader (e.g., 550nm) and a "Blue" shader (e.g., 450nm), each with its own slightly different IOR.
    
5. Finally, you would use Combine RGB to reassemble the results of these three separate shader paths.
    
6. The result, when light passes through the object, is that the red, green, and blue components of the light will refract at slightly different angles, splitting apart to create the characteristic rainbow "fire" seen in diamonds or the spectrum from a prism. The Wavelength node is critical to this process as it provides the pure, physically-correct spectral colors needed for each calculation path.