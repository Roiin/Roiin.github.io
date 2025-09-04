**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** This is a legacy procedural noise generator whose functionality has been fully integrated into the modern Noise Texture node as different noise Type options.

**Key Properties & Settings:**  
To access the Musgrave functionality, add a standard Noise Texture node. The Musgrave patterns are available by changing the Type property to one of the following, which create complex noise by layering multiple octaves of Perlin noise:

- **Type:** Switches the algorithm used. The Musgrave types are:
    
    - **fBM (Fractal Brownian Motion):** The standard, versatile multifractal noise.
        
    - **Multifractal:** Creates noise with more fine detail and contrast.
        
    - **Hybrid Multifractal:** Creates sharp peaks and valleys, excellent for mountain ranges or jagged terrain.
        
    - **Ridged Multifractal:** Creates sharp ridges, ideal for certain types of noise and organic patterns.
        
    - **Hetero Terrain:** A variation of Hybrid Multifractal often used for generating realistic terrain.
        
- **Detail:** Controls the number of noise layers (octaves) that are added together. Higher values create more fine, intricate detail.
    
- **Roughness:** Controls the influence of each successive layer of noise. Higher roughness values create more chaotic, "rough" detail.
    

**Practical Application:**  
The various Musgrave-style noise types within the Noise Texture node are unparalleled for creating complex, naturalistic patterns with detail at multiple scales. They are perfect for generating realistic **rust** corrosion.

The problem with using a simple, standard noise is that it often creates soft, uniform blobs. Real rust is a chaotic, layered process with large patches of discoloration, smaller pitted areas, and fine, grainy textures all coexisting. You need a noise that can capture this multi-layered complexity. The solution is to use a Noise Texture set to a Multifractal type.

1. Create two Principled BSDF shaders for "Painted Metal" and "Rust". Use a Mix Shader to blend them.
    
2. Add a Noise Texture and set its Type to Multifractal.
    
3. Connect the Factor output of the Noise Texture through a ColorRamp (to create a high-contrast mask) and into the Fac of the Mix Shader.
    
4. The multifractal algorithm will now generate a mask that is not uniform. It will create large areas of rust, but within those areas, the high Detail will introduce smaller, more intricate sub-patterns. This mimics the way corrosion spreads, creating a far more believable and organic result than a simple noise ever could. This same texture can also be used to drive the Roughness and a Bump map to ensure the rust is physically rougher and more pitted than the clean paint.