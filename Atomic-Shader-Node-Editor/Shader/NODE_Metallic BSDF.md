**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Provides a specialized shader for creating physically-based metallic surfaces, offering both artist-friendly and scientifically accurate models for controlling reflections.

**Key Properties & Settings:**

- **Fresnel Type:** The primary control that switches the node between two distinct modes.
    
    - **F82 Tint:** An artist-friendly model. It uses a Base Color for the main reflection color and an Edge Tint to control the color shift at grazing angles. This is intuitive but not physically precise.
        
    - **Physical Conductor:** A scientifically accurate model. It requires you to input the complex Index of Refraction (IOR for the n value and Extinction for the k value) for a real-world metal. This is the mode to use for maximum realism.
        
- **Roughness (Input):** Controls the sharpness of the reflection. A value of 0.0 creates a perfect mirror, while higher values create a blurrier, more matte finish.
    
- **Anisotropy [Cycles Only]:** Stretches highlights to simulate the effect of brushed or spun metal.
    
- **Tangent [Cycles Only]:** An input that takes a vector to control the direction of the Anisotropy effect, typically from a Tangent node.
    
- **BSDF (Output):** The standard shader output.
    

**Practical Application:**  
While the Principled BSDF is excellent for general-purpose metals, the Metallic BSDF is the superior tool when scientific accuracy is paramount. Imagine you are creating a high-fidelity product visualization of a solid gold ingot.

The problem is that "gold" isn't just a simple yellow color; it has a complex and specific way of reflecting different wavelengths of light that gives it its characteristic luster. Faking this with a simple color can look like cheap plastic. The Metallic BSDF is the solution for achieving true-to-life accuracy.

1. Add a Metallic BSDF node and set its Fresnel Type to Physical Conductor.
    
2. You now need real-world optical data for gold. From a scientific source (like refractiveindex.info), you find the IOR (n) and Extinction (k) values for gold across the visible spectrum (Red, Green, and Blue wavelengths).
    
3. Enter these three-channel values directly into the IOR and Extinction color sockets on the node.
    
4. Set the Roughness to a very low value for polished gold.
    
5. The result is no longer an approximation. The shader is now calculating light reflection using the exact same physical properties as real gold, producing a material with unparalleled realism that correctly responds to any lighting condition. This is the professional workflow for creating scientifically accurate metals.