- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates Gabor noise, a procedural texture characterized by random, interleaved bands. Unlike standard noise, Gabor noise can be made highly directional (Anisotropic), making it ideal for patterns that have a clear "flow" or "grain."
    
- **Key Properties & Settings:**
    
    - **Vector (Socket - Input):** The coordinate space to evaluate the noise in.
        
    - **Scale (Socket - Input):** Controls the overall size and density of the noise pattern.
        
    - **Frequency (Socket - Input):** Controls the rate of change perpendicular to the noise bands, effectively making the bands thicker or thinner.
        
    - **Anisotropy (Socket - Input):** A float from 0 to 1. At 1.0, the noise bands are perfectly aligned in a single direction. At 0.0, the noise is omnidirectional, similar to standard noise.
        
    - **Orientation (Socket - Input):** In 3D mode, this vector controls the main direction of the noise bands when Anisotropy is greater than 0.
        
    - **Type (Property):** Switches between 2D and 3D evaluation.
        
    - **Value (Socket - Output):** The final noise result, a combination of phase and intensity.
        
    - **Phase (Socket - Output):** Outputs only the phase of the noise, resulting in clean, continuous bands without intensity variations.
        
    - **Intensity (Socket - Output):** Outputs only the intensity, useful for finding the "singularities" or points where the bands meet.
        
- **Practical Application:** The Phase output of Gabor noise is perfect for creating procedural textures that mimic natural, flowing patterns, like the muscle fibers on an animal or the grain of worked wood.
    
    1. **The Goal:** To create a subtle, procedural displacement on a creature's muscle group that follows the natural flow of the muscles.
        
    2. Start with the creature's mesh. You'll need its Tangent and Normal vectors to create a coordinate system that follows the surface. You can use these to build a custom Vector input for the noise.
        
    3. Use the Gabor Texture node. Set Anisotropy to a high value like 0.9 to make the pattern directional.
        
    4. You can use the mesh's Tangent vector as the Orientation. This will make the noise bands flow along the natural direction of the mesh's UVs or topology, which often aligns with muscle flow.
        
    5. Use the Phase output. It creates clean, uniform waves. You can feed this into a Math node set to 'Sine' or use a Color Ramp to shape it into a series of ridges.
        
    6. Use this final value to drive the Offset Scale of a Set Position node (with the Normal as the direction).
        
    7. **The Result:** A subtle displacement effect that looks like muscle striations, flowing realistically across the creature's surface. The high anisotropy of the Gabor noise prevents it from looking like random bumpy skin and instead gives it a clear, organic directionality.