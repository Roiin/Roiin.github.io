- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- **Core Function:** Generates a versatile and organic-looking procedural noise (specifically, fractal Perlin noise). It is the fundamental building block for creating a vast range of natural effects like clouds, smoke, fire, dirt, and any other non-uniform, chaotic pattern.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** The input texture coordinates.
        
    - **4D (Mode) / W (Socket):** In 4D mode, the W socket acts as a "time" or "seed" value. Animating W causes the 3D noise pattern to evolve and change over time, which is essential for creating animated effects like boiling clouds or flickering fire.
        
    - **Scale (Socket):** Controls the overall size of the noise pattern. A higher value means smaller, finer details.
        
    - **Detail (Socket):** Adds more layers ("octaves") of finer detail on top of the base noise. Higher values create a more complex and intricate texture.
        
    - **Roughness (Socket):** Controls the influence of the higher-detail octaves. A high roughness creates a sharper, rougher texture, while a low roughness creates a smoother, softer look.
        
    - **Distortion (Socket):** Applies a second layer of noise to warp the main pattern, creating swirling, turbulent effects.
        
- **Outputs:**
    
    - **Factor (Socket):** The grayscale output of the noise. This is the most commonly used output.
        
    - **Color (Socket):** A color version where each RGB channel contains a different noise pattern. Useful for creating more complex color variations.
        
- **Practical Application:** Noise is the "atom" of chaos. If you need something to look less perfect, less uniform, or more natural, the Noise Texture is almost always the starting point.
    
    - **Molecular (Clouds, Smoke, Fog):** This is its most common use.
        
        1. Create a Noise Texture. Adjust the Scale for the cloud size and increase the Detail for texture.
            
        2. Feed the Factor output into a Color Ramp to control the contrast and density of the clouds.
            
        3. To animate it, set the mode to 4D and animate the W value. The clouds will now boil and evolve realistically.
            
    - **Molecular (Fire and Energy):**
        
        1. Use a Noise Texture with a high Roughness and some Distortion.
            
        2. Feed the Factor into a "fire" gradient on a Color Ramp (Black -> Red -> Orange -> Yellow -> White).
            
        3. Animate the texture coordinates or the W value to make the fire flicker and move.
            
    - **Organic (Adding Imperfection / Grunge):** CG renders are often too perfect. Noise is the solution.
        
        1. Create a Noise Texture with high Detail.
            
        2. Use a Color Ramp to crush its output into a high-contrast black and white pattern. This is now a "grunge map."
            
        3. Use this map as the Factor in a Mix node to subtly blend a dirt color over your clean render, or use it as a roughness map to break up perfect reflections.
            
    - **Organic (Heat Distortion / Water Ripples):**
        
        1. Create a large-scale, low-detail Noise Texture.
            
        2. Animate its W value slowly to make it warp over time.
            
        3. Feed the Factor output of this animated noise into the Vector socket of a Displace node.
            
        4. Place the Displace node over your final image. The result is a shimmering, wavy distortion effect perfect for heat haze, underwater caustics, or looking through imperfect glass.