**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee] (Note: Some Phase functions are Cycles Only)  
**Node Group:** Shader

**Core Function:** Provides a scientifically-focused interface for creating volumetric effects by directly inputting the physical coefficients for absorption, scattering, and emission, often from real-world measured data.

**Key Properties & Settings:**

- **Volume (Output):** The standard shader output, which must be connected to the Volume input of a Material Output or World Output node.
    
- **Absorption Coefficients (Input):** Directly sets the probability that light is absorbed per unit of distance. This is a technical input for users who have precise scientific data for a medium.
    
- **Scatter Coefficients (Input):** Directly sets the probability that light is scattered per unit of distance.
    
- **Emission Coefficients (Input):** Directly sets the amount of light emitted per unit of distance.
    
- **Scattering Controls:** This node also shares the advanced scattering controls found in the Volume Scatter node, such as Anisotropy and the various Phase functions (e.g., Rayleigh, Mie), which are primarily used in Cycles for advanced physical simulations.
    

**Practical Application:**  
This node is designed for technical and scientific visualization where accuracy is more important than artistic convenience. Imagine you are a scientific illustrator tasked with rendering a cross-section of the ocean, and you need to accurately depict the difference between clear, open-ocean water and murky, algae-rich coastal water based on data from an oceanography textbook.

The problem is that using artist-driven nodes like Volume Scatter and Volume Absorption would require you to guess the Color and Density settings to try and match the scientific data. This is imprecise and not verifiable. The Volume Coefficients node is the solution for this scenario.

1. From your scientific source, you obtain the precise spectral absorption and scattering coefficients for the target water type. This data specifies exactly how much red, green, and blue light is absorbed or scattered per meter of water.
    
2. Instead of picking a "blue" color, you input the three-channel scientific data directly into the Absorption Coefficients and Scatter Coefficients sockets.
    
3. The result is not an artistic approximation of "blue water" but a physically-based simulation. The final rendered appearance of the water—its specific color, depth, and clarity—is an emergent property of the real-world data you've provided. This allows you to create scientifically accurate visualizations that would be impossible to achieve reliably through artistic guesswork alone.