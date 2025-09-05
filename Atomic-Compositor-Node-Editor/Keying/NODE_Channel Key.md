- **Editor:** Compositor Node Editor
    
- **Node Group:** Keying
    
- **Core Function:** Generates a matte by isolating a range of values within a single, specific color channel (e.g., only the Red channel, or only the Luminance channel). It is a highly technical and precise keyer for situations where a clear separation exists in one channel but not necessarily in the overall color.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Color Space (Property):** Selects the color model to work in (RGB, HSV, YUV, YCbCr). This determines which channels are available for keying. YUV and YCbCr are often best for luminance-based keying.
        
    - **Channel (Property):** Selects the specific channel within the chosen color space that will be used for the key (e.g., R, G, B, or Y for Luminance).
        
    - **High (Socket):** The upper threshold. Values in the key channel below this threshold will be considered part of the matte (foreground).
        
    - **Low (Socket):** The lower threshold. Values in the key channel above this threshold will be considered part of the matte (foreground). Note: The naming can be confusing; think of it as defining the range to be kept.
        
- **Outputs:**
    
    - **Image (Socket):** The original image with the new alpha channel applied (premultiplied).
        
    - **Matte (Socket):** The raw black-and-white grayscale matte itself. This is often the more useful output, as it allows for further refinement before being applied.
        
- **Practical Application:** This is a specialist's keyer, perfect for pulling mattes from footage with strong color or brightness separation.
    
    - **Molecular (Explosion Keying / Luma Key):** This is its classic use case. Stock footage of explosions is often filmed against a black background.
        
        1. Set the Color Space to YCbCr and the Channel to Y (Luminance).
            
        2. Adjust the High and Low thresholds to isolate only the brightest parts of the image—the fire and smoke.
            
        3. The Matte output will be a perfect mask of the explosion, ready to be composited over your scene. This is a form of "Luma Keying."
            
    - **Molecular (Blue Sky Replacement):** For a shot with a vibrant, pure blue sky that needs to be replaced.
        
        1. Set the Color Space to RGB and the Channel to B (Blue).
            
        2. Adjust the High and Low values to create a matte that selects only the high-value blue pixels of the sky.
            
        3. Invert the resulting matte, and you have a clean mask for your sky replacement. This can often be cleaner than a Color Key if other objects in the scene are also blue but have a different brightness.
            
    - **Organic (Red Channel Skin Matte):** The red channel of human skin tones often contains unique information.
        
        1. Set the Color Space to RGB and Channel to R.
            
        2. By carefully adjusting the thresholds, you can sometimes pull a surprisingly detailed matte of just the skin, excluding hair and clothing, which can be used for targeted skin tone corrections.