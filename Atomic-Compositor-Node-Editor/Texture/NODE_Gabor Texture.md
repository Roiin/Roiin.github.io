- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- **Core Function:** Generates a highly controllable, procedural noise characterized by random, interleaved bands. It excels at creating directional patterns like wood grain, sand dunes, or brushed metal, offering a more structured and anisotropic alternative to the standard Noise Texture.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** The input texture coordinates.
        
    - **Scale (Socket):** Controls the overall size of the noise pattern.
        
    - **Frequency (Socket):** Adjusts the density of the bands, perpendicular to their flow. Higher frequency means more bands.
        
    - **Anisotropy (Socket):** The key directional control. A value of 1.0 creates perfectly parallel, directional bands. A value of 0.0 creates omnidirectional, cellular noise. Values in between create a mix of flowing and chaotic patterns.
        
    - **Orientation (Socket):** Sets the angle (in degrees for 2D) of the directional bands when Anisotropy is high. This can be driven by another texture to create swirling patterns.
        
- **Outputs:**
    
    - **Value (Socket):** The combined Gabor noise result. Good for a quick, general-purpose noisy texture.
        
    - **Phase (Socket):** Outputs only the smoothly flowing bands of the noise, without any random intensity variations. This is the most useful output for creating structured, organic patterns.
        
    - **Intensity (Socket):** A map of the noise's "energy" or contrast. It's black where the Phase bands meet or break, which is useful for masking out artifacts.
        
- **Practical Application:** Gabor noise is an advanced "atom" for creating sophisticated, naturalistic, and often directional procedural textures.
    
    - **Molecular (Brushed Metal / Wood Grain):** This is a classic use case.
        
        1. Set Anisotropy to 1.0.
            
        2. Use the Phase output. Adjust the Frequency and Scale to get the desired density of grain.
            
        3. Run the Phase output through a Color Ramp to create the final color and contrast for your wood or metal texture.
            
    - **Molecular (Sand Dunes / Fingerprints):** The Phase output naturally creates patterns of flowing, parallel lines with occasional breaks. By using a very high Frequency and a Color Ramp to create sharp black-and-white lines, you can generate patterns that strongly resemble desert sand dunes or the whorls of a fingerprint.
        
    - **Organic (Flowing Energy / Magical Auras):** The Orientation socket is the key to creating dynamic, swirling patterns.
        
        1. Create a base Gabor Texture with high Anisotropy.
            
        2. On a separate branch, create a Noise Texture with a very low frequency (large, soft blobs).
            
        3. Use a Map Range node to map the Noise Texture's output (0 to 1) to an angle range (e.g., 0 to 180 degrees).
            
        4. Feed this animated, noisy angle into the Orientation socket of the Gabor Texture.
            
        5. The result is a texture where the "grain" of the Gabor noise follows the soft, swirling pattern of the Noise Texture, perfect for creating flowing magical energy, Jupiter-like gas clouds, or abstract motion graphics.
            
    - **Organic (Cleaning Up Artifacts):** The Intensity output is a utility for perfecting the Phase output. Sometimes, the Phase output has undesirable "singularities" (points where the bands meet chaotically). The Intensity output is conveniently black in these exact spots. By Multiplying the Phase output with the Intensity output, you can fade out these artifact-prone areas, resulting in a cleaner final pattern.