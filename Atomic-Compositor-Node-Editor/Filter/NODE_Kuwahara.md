- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** An advanced, edge-preserving smoothing filter designed to reduce texture detail and noise while maintaining sharp outlines. Its Anisotropic mode is particularly effective at creating a stylized, "painterly" or "brush stroke" effect.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Variation (Property):** The core algorithm selection.
        
        - Classic: A faster, simpler version that produces a blocky, slightly posterized smoothing effect.
            
        - Anisotropic: The more powerful and artistic version. It analyzes the "flow" of edges and orients the smoothing effect along them, creating the characteristic brush stroke look.
            
    - **Size (Socket):** Controls the radius of the smoothing effect. Larger sizes create broader "brush strokes" and more abstraction, but can be slow to compute.
        
    - **Sharpness (Socket):** (Anisotropic only) Controls how crisply the edges are preserved. Higher values result in sharper, more defined outlines between smoothed areas.
        
    - **Eccentricity (Socket):** (Anisotropic only) Controls the shape of the "brush strokes." A low value creates round, circular patterns, while a high value creates long, thin, directional strokes.
        
- **Practical Application:** This is not a utility node for subtle fixes; it's a powerful "atom" for creating a distinct, non-photorealistic art style.
    
    - **Molecular (Painterly Look):** This is its primary and most impressive use.
        
        1. Set the Variation to Anisotropic.
            
        2. Increase the Size to a moderate value (e.g., 5-10) to start seeing the effect.
            
        3. Adjust the Eccentricity and Sharpness to define the character of your "painting"—do you want long, flowing strokes or short, dabbed ones?
            
        4. By chaining multiple Kuwahara nodes together (applying the effect iteratively), you can further abstract the image, making it look even more like an oil painting.
            
    - **Molecular (Toon Shader / Cel Shading Base):** The Kuwahara filter can be a key component of a compositing-based toon shader.
        
        1. First, use a Posterize node to reduce the image's color palette to a few flat shades.
            
        2. Then, apply the Kuwahara filter. This will smooth the transitions between the posterized color bands in a stylized way, cleaning up jagged edges and giving the flat colors a clean, painted-on appearance.
            
    - **Organic (Animated "Living Painting"):** To create a stunning animated effect, you can combine the Kuwahara filter with procedural noise.
        
        1. Apply the Kuwahara filter to your footage to create the base painterly look.
            
        2. Separately, create an animated, low-frequency Noise texture.
            
        3. Use a Displace node. Connect the Kuwahara-filtered image to the Image socket and the animated Noise texture to the Vector socket.
            
        4. The result is a "living painting" where the brush strokes appear to subtly shimmer and move, a highly sophisticated and eye-catching visual effect.