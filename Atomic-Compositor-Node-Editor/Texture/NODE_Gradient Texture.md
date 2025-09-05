- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- **Core Function:** Generates a variety of simple, smooth procedural gradients (linear, radial, spherical). It is a foundational "atom" for creating ramps, masks, and control maps for other nodes.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** The input texture coordinates that the gradient is based on. If left unconnected, it uses the screen's coordinate system.
        
    - **Gradient Type (Property):** Selects the shape and direction of the gradient.
        
        - Linear: A standard ramp from black to white along the X-axis.
            
        - Quadratic/Easing: Variations of the linear ramp with different falloff curves (ease-in/ease-out).
            
        - Diagonal: A ramp that runs from the bottom-left corner to the top-right.
            
        - Spherical: A circular gradient that is white at the center (0,0,0) and fades to black outwards.
            
        - Radial: An angular gradient that sweeps around the Z-axis, like a clock face or a color wheel's hue strip.
            
- **Outputs:**
    
    - **Color (Socket):** The gradient represented as a color.
        
    - **Factor (Socket):** The gradient represented as a grayscale value. This is the most commonly used output.
        
- **Practical Application:** While simple on its own, the Gradient Texture is almost always used as a controller or mask for more complex effects. It's the starting point for countless "molecules."
    
    - **Molecular (Simple Wipe Transitions):**
        
        1. Use a Linear gradient.
            
        2. Feed its Factor output into a Color Ramp node.
            
        3. By animating the position of the color stops on the ramp, you can create a black-and-white mask that smoothly wipes across the screen.
            
        4. Use this animated mask as the Factor in a Mix node to transition between two video clips.
            
    - **Molecular (Procedural Vignette):** The Spherical gradient is perfect for this.
        
        1. Use a Spherical gradient. It will be a white circle in the center of your screen.
            
        2. Feed its Factor output into a Color Ramp and invert the colors (white stop on the left, black on the right).
            
        3. You now have a black circle in the center that fades to white at the edges. Adjust the color stops to control the size and softness of your vignette mask.
            
    - **Organic (Faking a Sunset Sky):** You can build a simple but effective sky "molecule."
        
        1. Take a Linear gradient. Use a Mapping or Texture Coordinate node to rotate it so it runs vertically (bottom to top).
            
        2. Feed this vertical gradient into a Color Ramp.
            
        3. In the Color Ramp, create the color palette of a sunset: a dark blue at the bottom, transitioning to a deep orange, then a bright yellow near the horizon line.
            
        4. The result is a fully procedural, animatable sunset sky that can be used as a background.
            
    - **Organic (Creating a Radar Sweep):** The Radial gradient is ideal for this.
        
        1. Take the Radial gradient's Factor output.
            
        2. Feed it into a Math node set to Multiply. Animate the second value to make the gradient "spin."
            
        3. Feed the result into a Color Ramp with a very sharp, thin white line on an otherwise black ramp.
            
        4. The result is a thin white line that rotates around the center of the screen, just like a radar sweep.