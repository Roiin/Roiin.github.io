- **Editor:** Compositor Node Editor
    
- **Node Group:** Converter (Mix)
    
- **Core Function:** Reconstructs a full-color image from its individual component channels. It is the inverse of the Separate Color node and is essential for workflows that involve manipulating a single channel (like Alpha or Luminance) independently before reassembling the final image.
    
- **Key Properties & Settings:**
    
    - **Mode (Property):** Determines the color model used for combining the channels. The input sockets change dynamically based on this setting. Common modes include:
        
        - RGB: Combines Red, Green, and Blue channels.
            
        - HSV: Combines Hue, Saturation, and Value channels.
            
        - YCbCr: Combines Luminance (Y) and two Chrominance (color difference) channels.
            
    - **Alpha (Socket):** A grayscale input for the image's transparency channel. This socket is always present regardless of the mode.
        
    - **Color Channel Sockets:** The three main input sockets which change based on the mode (e.g., R, G, B or H, S, V).
        
- **Practical Application:** This node's power is never used in isolation; it is always the final step in a "Separate -> Manipulate -> Combine" chain, which unlocks incredibly powerful and precise image modifications.
    
    - **Molecular (Edge Softening / Blurring Alpha):** A classic technique to help a CG element sit better in a scene.
        
        1. Use a Separate RGBA node on your render.
            
        2. Take the Alpha output and feed it into a Blur node with a small value (e.g., 2 pixels).
            
        3. Use a Combine RGBA node. Reconnect the original R, G, and B channels, but use the new, blurred Alpha for the Alpha input.
            
        4. The result is an object with slightly softened edges, which helps to fake atmospheric haze and removes the sharp "CG look."
            
    - **Organic (Luminance-Based Brightness Control):** A more photorealistic way to brighten an image without oversaturating the colors.
        
        1. Separate Color in YCbCr mode.
            
        2. Take the Y (Luminance) channel and feed it into a Math node set to Multiply (e.g., by 1.2) or into an RGB Curves node for more control.
            
        3. Combine Color in YCbCr mode. Reconnect the modified Y channel with the original Cb and Cr channels.
            
        4. This "molecule" brightens the image's light values without affecting the color information, often producing a more pleasing result than simply increasing the Value in an HSV model.
            
    - **Organic (Procedural Chromatic Aberration):** To simulate a realistic lens distortion effect:
        
        1. Separate RGBA on your final image.
            
        2. Take the R channel and use a Transform node to scale it slightly (e.g., Scale: 1.002).
            
        3. Take the B channel and use a Transform node to scale it in the opposite direction (e.g., Scale: 0.998). Leave the G channel untouched.
            
        4. Combine RGBA. Reconnect the scaled R, original G, and scaled B channels.
            
        5. The result is a subtle color-fringing at the edges of the frame that perfectly mimics the chromatic aberration of a real camera lens, significantly boosting realism.