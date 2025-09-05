- **Editor:** Compositor Node Editor  
- **Node Group:** Keying
    
- **Core Function:** Generates a matte by calculating the "distance" between each pixel's color and a chosen Key Color within a 3D color space. Pixels that are "close" to the key color are made transparent, while those that are "far away" remain opaque.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Key Color (Property):** The central color you want to remove. Use the color picker to select it from your image.
        
    - **Color Space (Property):** The 3D color space in which the "distance" is calculated. RGB is a simple cube, while YCC (YCbCr) separates brightness from color, which can sometimes produce better results by ignoring shadows.
        
    - **Tolerance (Socket):** Defines the "radius" of the key. It's the maximum distance a pixel can be from the Key Color and still be considered part of the key. A higher tolerance selects a wider range of similar colors.
        
    - **Falloff (Socket):** Controls the softness of the edge of the key. A higher falloff creates a smoother, more gradual transition between the keyed and un-keyed areas.
        
- **Outputs:**
    
    - **Image (Socket):** The original image with the new alpha channel applied.
        
    - **Matte (Socket):** The raw black-and-white grayscale matte.
        
- **Practical Application:** This node offers a very intuitive, "single slider" approach to keying, which can be surprisingly effective for pulling mattes from complex, multi-colored backgrounds where other keyers might struggle.
    
    - **Molecular (Secondary Color Correction Masking):** Like the Color Key node, this is one of its strongest uses. If you want to isolate all the "warm tones" in an image to make them more vibrant:
        
        1. Pick a representative orange or yellow from the image as your Key Color.
            
        2. Increase the Tolerance until the Matte output shows all the desired warm areas (skin tones, sunsets, fire) as white.
            
        3. You can now use this matte to drive a Saturation boost that affects only those warm colors. The "distance" logic is good at grabbing a whole family of related colors.
            
    - **Molecular (Garbage Matte for Busy Backgrounds):** Imagine your subject is in front of a green screen, but also partially in front of a blue wall. A simple greenscreen keyer won't work.
        
        1. Use a Distance Key node. Pick the blue of the wall as the Key Color. Adjust the Tolerance to key out just the wall.
            
        2. Use a second keyer (like Chroma Key) to handle the green screen.
            
        3. Combine the two mattes. This allows you to remove a multi-colored background in stages.
            
    - **Organic (YCC Mode for Shadow Immunity):** The YCC color space is a powerful feature. It primarily calculates distance based on the two chroma (color) channels, largely ignoring the Y (luma/brightness) channel.
        
        1. Set the Color Space to YCC.
            
        2. Pick your green screen color.
            
        3. Now, the node will key out the green color regardless of whether it's in a bright area or a deep shadow, because it's looking at the "green-ness," not the brightness. This can be a very effective way to pull a clean key from an unevenly lit screen with a single node.