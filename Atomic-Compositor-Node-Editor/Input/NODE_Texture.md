- **Editor:** Compositor Node Editor
    
- **Node Group:** Input  
    -- **Core Function:** Generates a 2D image from one of Blender's internal procedural textures (e.g., Clouds, Noise, Voronoi), making complex, resolution-independent patterns available for compositing tasks.
    
- **Key Properties & Settings:**
    
    - **Texture Data-Block (Property):** A menu to select a pre-existing texture that has been created in the Texture Properties panel. The texture's own settings (like noise type, size, depth) are edited there, not within this node.
        
    - **Offset (Socket):** A 3D vector to shift the texture's origin. Animating the Z value is a common way to evolve a 2D noise pattern over time.
        
    - **Scale (Socket):** A 3D vector to control the size of the texture along the X, Y, and Z axes.
        
    - **Value (Socket):** Outputs the grayscale intensity of the texture.
        
    - **Color (Socket):** Outputs the color version of the texture, if one is defined (e.g., for some Blend types).
        
- **Practical Application:** This node is a powerhouse for creating procedural mattes, distortions, and organic effects without relying on external image files.
    
    - **Molecular (Procedural Dirt/Grunge Map):** To break the clean look of CG, you need imperfections.
        
        1. Create a Clouds or Musgrave texture.
            
        2. Use the Value output of the Texture node and pipe it into a Color Ramp to crush the whites and blacks, creating a high-contrast grunge map.
            
        3. Use this map as the Factor in a Mix node to subtly blend a dark, grimey color over your clean render, adding realistic wear and tear.
            
    - **Molecular (Animated Heat Distortion):**
        
        1. Create a Clouds texture. In the Texture node, animate the Z-value of the Offset over time to make the clouds "boil."
            
        2. Pipe the Value output of this animated texture into the Vector socket of a Displace node.
            
        3. Place the Displace node over your main image. The result will be a shimmering, wavy heat distortion effect, perfect for jet engines, desert horizons, or magical auras.
            
    - **Organic (Energy Shield / Force Field Effect):**
        
        1. Create a Voronoi texture (set to Distance to Edge) to generate a cellular pattern. Animate the Z-offset to make the pattern evolve.
            
        2. Take the Value output and use a Color Ramp to isolate just the thin cell borders, making them bright white on a black background.
            
        3. Feed this into a Glare node (set to Fog Glow) to make the lines bloom with energy.
            
        4. Finally, use a Mix node set to Add or Screen to composite this glowing, animated shield effect over your character or spaceship render.
            
    - **Organic (Procedural Gobo/Light Cookie):** Simulate light shining through a leafy tree or a patterned window.
        
        1. Create a Noise or Magic texture.
            
        2. Use this texture as a mask on a bright color (using a Mix node) and then blur it slightly to soften the edges.
            
        3. Composite this blurred pattern over your scene using Add or Screen to create the illusion of complex, patterned light and shadow that would be difficult to achieve with actual geometry.