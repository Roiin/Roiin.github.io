- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Adjusts the overall brightness of an image by simulating a camera's exposure control. It operates multiplicatively in linear color space, making it ideal for photorealistic adjustments and working with high dynamic range (HDR) images.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Exposure (Socket):** A value that adjusts the brightness in "stops." A value of 0.0 is no change. A value of +1.0 doubles the image brightness. A value of -1.0 halves the image brightness.
        
- **Practical Application:** This node is preferred over Brightness for any task that requires a physically plausible change in light intensity.
    
    - **Molecular (Primary Exposure Correction):** Its most common use is to correct an under- or over-exposed render. If your render is too dark, increasing the Exposure by 1.0 or 1.5 is often the first and best step to bringing it into a correct tonal range, as it behaves more like adjusting the shutter speed on a real camera.
        
    - **Molecular (Faking Light Flashes):** To create a convincing camera flash or lightning strike:
        
        1. Animate the Exposure value. For a single frame, push the value very high (e.g., 4.0 or 5.0) and then immediately bring it back to 0.0 on the next frame.
            
        2. This multiplicative effect will realistically "blow out" the highlights and brightly illuminate the scene for that one frame, mimicking how a real camera sensor would be overwhelmed by a sudden burst of light.
            
    - **Organic (Localized Lighting with Masks):** This is where it becomes a powerful artistic tool. Imagine a character walking through a dark room and passing by a window.
        
        1. Create an animated Mask that follows the area of light cast by the window onto the character.
            
        2. Use a Mix node. Connect the original image to the top socket and to an Exposure node. Connect the output of the Exposure node to the bottom socket. Use the animated mask as the Factor.
            
        3. Now, you can increase the Exposure value to create the effect of the character being brightly illuminated only when they are inside the masked area, realistically integrating them with the light source.
            
    - **Organic (HDR Workflow):** When working with high dynamic range imagery (like 32-bit EXR files), the Exposure node is essential. The image may contain color values far greater than 1.0 (e.g., for the sun or a light bulb filament). The Exposure node allows you to "bring down" the overall scene exposure to see these "hot" details, or "bring up" the exposure to see details hidden in the shadows, all without clipping or losing the valuable HDR data, which a simple Brightness control might do.