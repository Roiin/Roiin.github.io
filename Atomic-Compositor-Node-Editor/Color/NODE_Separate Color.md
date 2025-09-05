- **Editor:** Compositor Node Editor
    
- **Node Group:** Converter (Mix)
    
- **Core Function:** Deconstructs a full-color image into its individual component channels, outputting each as a separate grayscale image. This allows for the independent manipulation of specific aspects of an image, like its red content, its brightness, or its transparency.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be deconstructed.
        
    - **Mode (Property):** Determines the color model used for separating the channels. The output sockets change dynamically based on this setting. Common modes include:
        
        - RGB: Outputs Red, Green, and Blue channels.
            
        - HSV: Outputs Hue, Saturation, and Value (brightness) channels.
            
        - YCbCr: Outputs Luminance (Y) and two Chrominance (color difference) channels.
            
    - **Alpha (Socket):** A grayscale output for the image's transparency channel. This socket is always present regardless of the mode.
        
    - **Color Channel Sockets:** The three main output sockets which change based on the mode (e.g., R, G, B or H, S, V).
        
- **Practical Application:** This node is the first step in any advanced, channel-specific workflow. It is always used in a "Separate -> Manipulate -> Combine" chain.
    
    - **Molecular (Creating a Luminance Key):** One of the most common uses. To create a mask of the brightest parts of an image (a Luma Key):
        
        1. Set the Mode to HSV.
            
        2. Take the V (Value) output. This is a perfect grayscale representation of the image's brightness.
            
        3. Feed this V output into a Color Ramp node to crush the values and isolate only the brightest areas. The result is a high-quality Luma Key mask that can be used to drive a Glare node or a color correction effect.
            
    - **Molecular (Saturation-Based Masking):** To create a mask based on the most colorful parts of an image:
        
        1. Set the Mode to HSV.
            
        2. Take the S (Saturation) output. This grayscale image is white where the original image was most colorful and black where it was grayscale.
            
        3. This mask can be used, for example, to apply sharpening only to the colorful parts of an image, leaving less saturated areas softer.
            
    - **Organic (Red Channel-Based Blood/Vein Effect):** For a stylized horror or sci-fi effect on a character's face:
        
        1. Separate Color in RGB mode.
            
        2. Take the R (Red) channel output. In skin tones, this channel often highlights subsurface details like veins and blemishes.
            
        3. Use an RGB Curves or Color Ramp node to dramatically increase the contrast of this red channel, making the veins stand out as a dark network.
            
        4. You can then Multiply this creepy vein map back over the original skin tone or use it as a mask to color the veins a different color, all based on the data that was already hidden in the original image.
            
    - **Organic (Channel-Specific Denoising):** In video footage, the blue channel is often the noisiest. To denoise a shot without softening the entire image:
        
        1. Separate Color in RGB mode.
            
        2. Take the B (Blue) channel and run it through a Denoise or Blur node.
            
        3. Use a Combine Color node. Reconnect the original R and G channels, but use the new, cleaned-up B channel.
            
        4. This "molecule" selectively cleans the noisiest part of the image, preserving the crucial sharpness found in the green and red channels for a much better overall result.