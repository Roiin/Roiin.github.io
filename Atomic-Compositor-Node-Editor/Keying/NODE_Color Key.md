- **Editor:** Compositor Node Editor  
- **Node Group:** Keying
    
- **Core Function:** Generates a matte by isolating a specific color based on its Hue, Saturation, and Value (HSV) components. It allows for a more granular and often more intuitive selection of a color range compared to other keyers, making it useful for more than just greenscreen work.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The input image from which to pull the key.
        
    - **Key Color (Property):** Use the color picker to select the central target color you want to make transparent.
        
    - **Hue Tolerance (Socket):** Controls how far around the color wheel the selection will extend. A high value will select a wider range of hues (e.g., both greenish-blues and yellowish-greens).
        
    - **Saturation Tolerance (Socket):** Controls the range of color intensity to be selected. A high value will select both vibrant and muted versions of the key color.
        
    - **Value Tolerance (Socket):** Controls the range of brightness to be selected. A high value will select both dark and bright versions of the key color.
        
- **Outputs:**
    
    - **Image (Socket):** The original image with the new alpha channel applied (premultiplied).
        
    - **Matte (Socket):** The raw black-and-white grayscale matte. This is the preferred output for professional workflows as it allows for further refinement.
        
- **Practical Application:** While it can be used for greenscreens, its strength lies in pulling keys from less-than-perfect sources or for secondary color correction masking.
    
    - **Molecular (Secondary Color Correction Mask):** This is one of its best uses. Imagine you want to change the color of a character's red shirt.
        
        1. Connect your footage to the Color Key node.
            
        2. Use the Key Color picker to select the red of the shirt.
            
        3. Carefully adjust the Hue, Saturation, and Value tolerance sliders until the Matte output shows the shirt as a clean white shape against a black background.
            
        4. You can now use this matte as the Factor for a Hue Correct or Color Balance node to change the shirt's color without affecting the character's skin tone or the background.
            
    - **Molecular (Imperfect Greenscreen Keying):** If your greenscreen has uneven lighting (some parts are bright green, others are dark green), the Color Key node can be very effective.
        
        1. Pick a mid-tone green as your Key Color.
            
        2. Keep the Hue Tolerance relatively low to only select greens.
            
        3. Increase the Value Tolerance to a higher value. This will tell the node to key out the green color regardless of whether it's bright or dark, which is perfect for handling shadows on a greenscreen.
            
    - **Organic (Multi-Stage Keying):** You can use multiple Color Key nodes to build up a complex matte.
        
        1. **Node 1:** Pulls a key for the main, well-lit part of the greenscreen.
            
        2. **Node 2:** Is configured to pull a separate key for the darker, shadowy parts of the screen.
            
        3. **Node 3:** Pulls a key for a specific problematic reflection.
            
        4. Use Mix nodes (set to Add or Lighten) to combine the Matte outputs from all three nodes into a single, comprehensive final matte. This "organism" is far more robust than trying to get a perfect result from a single keyer.