- **Editor:** Compositor Node Editor  
- **Node Group:** Utilities
    
- **Core Function:** Performs a wide variety of mathematical operations on numerical inputs. It is the core logic unit for manipulating values, creating procedural animations, and building complex masks and effects.
    
- **Key Properties & Settings:**
    
    - **Operation (Property):** The master dropdown menu that selects the function to be performed. The inputs change dynamically based on the chosen operation.
        
    - **Value (Sockets):** One or more numerical input sockets.
        
    - **Clamp (Property Checkbox):** When available, this limits the output to the standard 0-1 range, which is essential for preventing unwanted behavior when creating masks or color values.
        
- **Outputs:**
    
    - **Value (Socket):** The single numerical result of the calculation.
        
- **Practical Application:** If nodes are a programming language, the Math node is the +, -, *, /, if, and then. It's used everywhere to control everything.
    
- **Common Operations & Their Uses:**
    
    - **Add / Subtract / Multiply / Divide:**
        
        - **Molecular (Adjusting Values):** These are the most basic operations. Use Multiply to increase the intensity of an effect (like making a luminance channel brighter). Use Add or Subtract to offset a value (like shifting the position from a tracker).
            
    - **Greater Than / Less Than:**
        
        - **Molecular (Creating Binary Masks):** These are thresholding tools. Feed a Depth pass into a Greater Than node with the second value set to 20. The output will be a perfect black-and-white mask of everything in your scene that is more than 20 meters away from the camera.
            
    - **Minimum / Maximum:**
        
        - **Molecular (Combining Masks):** These are the standard ways to combine two grayscale masks. Maximum is equivalent to a logical "OR" or an Add blend in Photoshop (it takes the brightest value from either mask). Minimum is equivalent to a logical "AND" or a Multiply blend (it takes the darkest value).
            
    - **Sine / Cosine:**
        
        - **Molecular (Procedural Oscillation):** To make an effect pulsate or oscillate smoothly. Feed a Scene Time node into a Sine function. The output will be a value that smoothly animates back and forth between -1 and 1, perfect for creating a pulsing glow, a gentle rocking motion, or a color-cycling effect.
            
    - **Modulo:**
        
        - **Molecular (Creating Repeating Patterns):** Modulo outputs the remainder of a division. When fed a linear gradient (like pixel coordinates), it creates a repeating sawtooth wave. This is the key to creating procedural scanlines, stripes, or grids. For example, using Modulo with the Y-coordinate can create perfect horizontal lines.
            
    - **Round / Floor / Snap:**
        
        - **Molecular (Posterizing / Quantizing):** These functions are used to "step" a smooth gradient into distinct blocks. Snap is particularly useful. If you feed a noise texture into a Snap node with an Increment of 0.25, the output will be a texture with only four distinct values (0, 0.25, 0.5, 0.75), creating a posterized look.