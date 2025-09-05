- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** Generates volumetric-looking light rays (also known as "crepuscular rays" or "god rays") that emanate from the bright areas of an image. It is a fast, 2D effect that simulates light scattering in a medium like fog or haze.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The input image that contains the bright light sources (e.g., the sun, a window, a flashlight beam).
        
    - **Source X/Y (Sockets):** The coordinates of the central point from which all beams will radiate. The position is a factor of the image size (0.5, 0.5 is the exact center).
        
    - **Ray Length (Socket):** Controls how far the beams extend from the source. A value of 1.0 can make them stretch across the entire image.
        
- **Practical Application:** This is the go-to node for adding dramatic, atmospheric lighting to a scene without the heavy render cost of true volumetric lighting.
    
    - **Molecular (Basic God Rays):** The most direct use case.
        
        1. Identify the location of your main light source (e.g., the sun, which might be off-camera). Set the Source X/Y coordinates to match this location.
            
        2. Take your rendered image and use an RGB Curves or Luma Key node to create a high-contrast mask that isolates only the brightest parts (e.g., the bright sky visible through tree branches).
            
        3. Feed this highlights-only mask into the Image socket of the Sun Beams node. This will generate clean, white light rays.
            
        4. Use a Mix node set to Add or Screen to combine these generated rays back on top of your original, full-color render.
            
    - **Organic (Integrating with Atmospherics):** For a more believable effect, the rays should interact with the scene's atmosphere.
        
        1. Create your god rays as described above.
            
        2. Separately, create a fog/mist layer for your scene (e.g., using the Mist pass or a procedural Noise texture).
            
        3. Use a Mix node set to Multiply. Connect the fog layer to one socket and the sunbeam layer to the other.
            
        4. This "molecule" ensures that the sunbeams are only visible where there is also fog, creating a much more integrated and realistic effect. Add this final result back over your main image.
            
    - **Organic (Animating Rays for Motion Graphics):** The Source coordinates are animatable, which is great for motion graphics.
        
        1. Take a piece of text or a logo with a bright emissive material.
            
        2. Feed it into the Sun Beams node.
            
        3. Animate the Source X/Y coordinates to move around the screen.
            
        4. The result will be dramatic light rays that sweep and pan across the text, creating a dynamic and high-energy title reveal.