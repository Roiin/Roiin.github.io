- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- **Core Function:** Generates a procedural pattern of parallel bands (lines) or concentric rings. It includes built-in noise controls to easily add distortion and organic variation to the patterns.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** Input for the texture coordinates.
        
    - **Type (Property):** The master control for the pattern shape.
        
        - Bands: Creates parallel, straight lines.
            
        - Rings: Creates concentric circles.
            
    - **Direction (Property):**
        
        - For Bands, sets the orientation of the lines (X, Y, or Diagonal).
            
        - For Rings, sets the origin and shape (X, Y, Z, or Spherical for a 3D effect).
            
    - **Wave Profile (Property):** Controls the falloff of the waves. Sine creates a smooth, soft-edged wave (like a sine wave), while Saw creates a hard-edged, linear ramp (a sawtooth wave).
        
    - **Scale (Socket):** Controls the frequency or density of the bands/rings. A higher scale means more, thinner lines.
        
    - **Distortion (Socket):** The key artistic control. It applies a built-in noise pattern to the waves, breaking up the perfect straight lines or circles and making them look more organic and chaotic.
        
    - **Detail / Detail Scale / Roughness (Sockets):** Controls the characteristics of the Distortion noise, allowing for fine-tuning of its complexity and texture.
        
    - **Phase Offset (Socket):** Shifts the position of the waves, allowing for easy animation of the pattern moving or pulsing.
        
- **Outputs:**
    
    - **Color (Socket):** A colorized version of the pattern (often has artifacts, Factor is preferred).
        
    - **Factor (Socket):** A clean, grayscale output of the wave pattern. This is the most useful output.
        
- **Practical Application:** The Wave Texture is the "atom" of linear and circular repetition. It's the basis for wood grain, ripples, scanlines, and many sci-fi effects.
    
    - **Molecular (Wood Grain):** This is a classic "molecule."
        
        1. Set the Type to Bands.
            
        2. Set the Wave Profile to Saw.
            
        3. Add a small amount of Distortion with a high Detail Scale to create the characteristic wobbly, organic lines of wood grain.
            
        4. Feed the Factor output into a Color Ramp with a wood color palette (e.g., various shades of brown) to create the final texture.
            
    - **Molecular (Water Ripples):**
        
        1. Set the Type to Rings and Direction to Spherical.
            
        2. Set the Wave Profile to Sine for a soft, natural falloff.
            
        3. Feed the Factor output into a Bump or Displace node to create the appearance of ripples emanating from a central point. Animating the Phase Offset will make the ripples expand outwards.
            
    - **Organic (Sci-Fi Scanlines / Shield Effect):**
        
        1. Set the Type to Bands and Direction to Y for horizontal lines.
            
        2. Set the Wave Profile to Saw. Feed the Factor into a Color Ramp with a very thin, bright line on a black background.
            
        3. Animate the Phase Offset to make the scanline move down the screen.
            
        4. To make a "shield impact" effect, use a Rings type instead and animate the Phase Offset so the rings expand rapidly from the point of impact.
            
    - **Organic (Contour Lines / Topographic Map):**
        
        1. Take the Z component of your object's Generated or Object coordinates.
            
        2. Feed this into the Vector input of a Wave Texture node set to Bands.
            
        3. The node will now create bands that follow the height contours of your object. Feed the Factor into a Color Ramp with a Constant interpolation to create distinct, hard-edged contour lines, just like a topographic map.