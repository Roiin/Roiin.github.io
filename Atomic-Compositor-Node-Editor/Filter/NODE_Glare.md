- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** Analyzes the brightest parts of an image and generates physically-inspired light artifacts such as bloom, glows, and lens flares. It is a critical tool for adding photorealism and cinematic style to a render by simulating how a real camera lens handles intense light.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Glare Type (Property):** The master control that selects the effect's algorithm:
        
        - Fog Glow: A soft, high-quality, and realistic circular bloom. Often the best starting point.
            
        - Bloom: A simpler, faster but less physically-accurate glow.
            
        - Streaks: Creates cinematic lens flare streaks.
            
        - Simple Star: Creates a basic starburst effect.
            
        - Ghosts: Simulates internal lens reflections.
            
    - **Threshold (Socket):** Defines how bright a pixel must be to generate a glare effect. A low value (e.g., 0.8) will make many parts of the image glow, while a high value (e.g., 5.0) will restrict the effect to only the most intense highlights like the sun or lightbulb filaments.
        
    - **Mix (Property):** Blends the glare effect with the original image. A value of 0 shows the glare, -1 shows the original, and 1 shows the glare added to the original.
        
    - **Size (Socket):** Controls the overall size and spread of the glare effect (for Fog Glow, Streaks, etc.).
        
    - **Streaks (Socket):** For Streaks type, sets the number of flare streaks (e.g., 4 for a classic anamorphic flare).
        
- **Practical Application:** This single "atom" is responsible for adding the final layer of polish and realism to most renders. It turns a flat CG image into a believable photograph.
    
    - **Molecular (Basic Bloom):** The most common use.
        
        1. Set the Glare Type to Fog Glow.
            
        2. Lower the Threshold until your scene's main light sources and bright reflections begin to glow softly.
            
        3. Adjust the Size to control how far the glow spreads. This one simple step can dramatically increase the perceived brightness and energy of your lighting.
            
    - **Molecular (Anamorphic Lens Flare):** To create the iconic horizontal blue flare seen in many sci-fi and action films:
        
        1. Set the Glare Type to Streaks.
            
        2. Set Streaks to 2 or 4.
            
        3. Set the Angle Offset to 0 (for horizontal streaks).
            
        4. Use the Color Modulation property to introduce a blue tint to the flare.
            
        5. This "molecule" instantly adds a high-production-value cinematic feel.
            
    - **Organic (Layered Glare for Complexity):** Professional results often come from layering multiple glare effects.
        
        1. **Glare Node 1 (Bloom):** Use a Fog Glow with a low Threshold and medium Size. This creates a soft, foundational bloom on all the highlights.
            
        2. **Glare Node 2 (Streaks):** Take the output of the first node and feed it into a second Glare node set to Streaks. Use a much higher Threshold on this one.
            
        3. This "organism" creates a complex effect where all lights have a soft glow, but only the absolute brightest parts of the image (like the sun) will also cast the cinematic streaks, which is far more realistic and visually interesting than a single glare effect.
            
    - **Organic (God Rays):** The Fog Glow type is essential for creating volumetric light rays (God Rays).
        
        1. First, use other nodes (like the Mist pass or a procedural texture) to create an "atmosphere" in your scene.
            
        2. Then, apply a Glare node set to Fog Glow. The glare will interact with the composited fog, causing the bright areas (like a window) to cast beautiful, volumetric-looking light rays that feel integrated with the scene's atmosphere.