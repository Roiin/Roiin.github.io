- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (Color)
    
- **Core Function:** Assembles a single color output from separate, individual channel inputs (like Red, Green, and Blue, or Hue, Saturation, and Value).
    
- **Key Properties & Settings:**
    
    - **Mode (Property):** The color model to use for combining the channels:
        
        - **RGB:** The most direct mode, using Red, Green, and Blue channels.
            
        - **HSV:** A more intuitive model for artists, using Hue (the color tint), Saturation (the color's intensity), and Value (the color's brightness).
            
        - **HSL:** Similar to HSV, but uses Lightness.
            
    - **Channel Inputs (Sockets):** Three float sockets that change based on the selected Mode (e.g., R, G, B).
        
    - **Alpha (Socket - Input):** An optional float input to control the transparency of the final color.
        
    - **Color (Socket - Output):** The final, combined RGBA color.
        
- **Practical Application:** The 'HSV' mode is incredibly powerful for creating procedural color variations with artistic control, like the iridescent feathers on a hummingbird.
    
    1. **The Goal:** To make the color of the hummingbird's feathers shift based on the viewing angle, mimicking iridescence.
        
    2. You need to calculate the viewing angle. You can do this by taking the Dot Product of the camera's view vector and the surface Normal of the feathers. This gives you a value that changes as the camera moves around the bird.
        
    3. Use the Combine Color node set to 'HSV' mode.
        
        - **Hue:** Connect your calculated viewing angle value to the Hue input. As the angle changes, the hue will shift through the color spectrum (red, green, blue, etc.).
            
        - **Saturation:** You can connect a constant Value node set to 1.0 for vibrant, fully saturated colors.
            
        - **Value:** You can connect another constant Value node set to 1.0 for maximum brightness.
            
    4. The Color output is now a dynamic, shimmering color that changes with the viewing angle. Store this as a "feather_color" attribute.
        
    5. In your shader, use this attribute to drive the material's Base Color. The result is a stunning, realistic iridescence effect, created by procedurally driving just one channel (Hue) of the color.