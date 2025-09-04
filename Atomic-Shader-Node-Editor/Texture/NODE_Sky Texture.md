**Editor:** Shader Editor (World Context)  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Procedurally generates a physically-based, realistic sky and sun, providing a dynamic alternative to using a static HDRI.

**Key Properties & Settings:**

- **Color (Output):** The primary output, providing the color of the sky and sun. This should be connected to the Color input of a Background shader in the world node tree.
    
- **Sky Type (Property):** The core control that selects the underlying physical model. Nishita is the most modern and physically-accurate model, simulating atmospheric scattering for highly realistic results. Hosek/Wilkie is a popular alternative.
    
- **Sun Rotation / Sun Elevation (Properties):** The most frequently used controls. These two sliders allow you to interactively change the time of day and position of the sun in the sky, from a high noon to a low sunset.
    
- **Sun Intensity / Sun Size (Properties):** Controls the brightness and apparent size of the sun disc in the sky.
    
- **Altitude / Air / Dust (Properties):** These settings control the atmospheric conditions, allowing you to simulate anything from a clear, high-altitude sky to a hazy, polluted urban afternoon. Dust is particularly effective for creating warm, reddish sunsets as the virtual particles scatter blue light.
    

**Practical Application:**  
This node is invaluable when you need dynamic control over your scene's lighting, especially for animations or when you need to precisely match a sun position.

Imagine you are creating an architectural visualization of a house and need to show the client how it will look at different times of the day—morning, noon, and golden hour just before sunset. The problem is that using three separate HDRI files (one for each time of day) is inefficient and results in a jarring "pop" when switching between them in an animation. The Sky Texture node is the perfect solution.

1. In the World's shader editor, add a Sky Texture node and set its Type to Nishita.
    
2. Connect its Color output to the Color input of the Background shader.
    
3. Now, instead of loading a new image, you can simply animate the Sun Elevation and Sun Rotation properties. By keyframing Sun Elevation from a high value (e.g., 60°) down to a low value (e.g., 5°), you can create a seamless, physically-accurate time-lapse.
    
4. As the Sun Elevation decreases, the Nishita model will automatically and realistically shift the color of the sunlight from a cool white to a warm orange, lengthen the shadows, and change the ambient color of the sky from a deep blue to a fiery red. This provides a completely smooth, dynamic, and art-directable lighting solution that would be impossible with static image textures.