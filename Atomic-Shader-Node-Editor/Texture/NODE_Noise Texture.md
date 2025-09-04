**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a versatile, organic, pseudo-random pattern, which is the foundational building block for most procedural textures.

**Key Properties & Settings:**

- **Factor (Output):** The primary grayscale output, providing a cloudy, noisy pattern.
    
- **Color (Output):** Provides three independent noise patterns, one for each RGB channel, useful for creating more complex color variations.
    
- **Primary Controls:**
    
    - **Scale:** Controls the overall size or frequency of the noise pattern. Higher values create smaller, more detailed patterns.
        
    - **Detail:** Adds more layers (octaves) of finer noise on top of the base pattern, creating more intricate and complex results.
        
    - **Roughness:** Controls the influence of the higher-detail octaves, making the noise pattern appear smoother or more chaotic and "rough."
        
- **Dimensionality & Evolution:**
    
    - **Dimensions:** Sets the calculation space. 3D is the default for surfaces. 4D adds a W input.
        
    - **W (Input):** When using 4D, this acts as a "seed" or "time" value, allowing you to generate infinite variations of the noise pattern at the same location by changing the W value.
        
- **Distortion:** Warps or swirls the noise pattern, transforming the cloudy blobs into more fluid, turbulent shapes.
    

**Practical Application:**  
The Noise Texture is the workhorse of proceduralism, but its true power is unlocked when you manipulate its input coordinates. It is the perfect node for creating procedural **wood grain**.

The problem is that a default Noise Texture creates round, isotropic "cloud" patterns. Wood grain is made of long, stretched, anisotropic fibers. You need to transform the noise to match this shape. The solution is to use a Mapping node to stretch the texture's coordinates.

1. Start with a Noise Texture. Connect its Factor output through a ColorRamp to create the light and dark colors of the wood.
    
2. Add a Texture Coordinate node and connect its Generated or Object output to the Vector input of the Noise Texture.
    
3. Insert a Mapping node between the Texture Coordinate and the Noise Texture.
    
4. In the Mapping node, dramatically increase the Scale value on one axis (e.g., set X=1, Y=20, Z=1).
    
5. The result is immediate: the noise pattern is stretched 20 times along the Y-axis. The round, cloudy blobs are transformed into long, fibrous streaks that perfectly mimic the appearance of wood grain. By adjusting the Scale, Detail, and Distortion on the Noise Texture, you can create a huge variety of wood types, from smooth pine to a gnarled oak, all from this fundamental combination of nodes.