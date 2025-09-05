- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** A post-processing filter that attempts to smooth jagged, aliased edges ("jaggies") in an image. It uses edge detection to selectively blur only the harsh, stair-stepped lines without affecting the rest of the image.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input, which should ideally have aliasing artifacts.
        
    - **Filter Type (Property):** The algorithm used. MLAA (Morphological Antialiasing) is a modern and generally effective method. Older methods like FXAA are also available.
        
    - **Threshold (Socket):** Controls the sensitivity of the edge detection. Lower values will detect more subtle edges and apply more smoothing, while higher values will only target the most obvious jagged lines.
        
    - **Contrast Limit (Socket):** Helps the node distinguish between important high-contrast edges and less important low-contrast ones, which can reduce unwanted blurring on textures.
        
    - **Corner Rounding (Socket):** A value that helps the algorithm preserve the sharpness of corners, preventing them from being incorrectly rounded off by the smoothing process.
        
- **Practical Application:** This node is a problem-solver, not a general-purpose creative tool. It's used to clean up renders that, for whatever reason, could not be sufficiently anti-aliased at render time.
    
    - **Molecular (Fixing Low-Sample Renders):** This is its primary intended use. If you have a preview render done with very low render samples (e.g., 1 sample in Cycles), the edges will be extremely jagged. Running this render through the Anti-Aliasing node can produce a surprisingly clean result in seconds, making it a valuable tool for quick previews and look development without waiting for a full, high-sample render.
        
    - **Molecular (Cleaning Up Z-Depth Passes):** The Z-depth pass from a render is famously not anti-aliased. This results in hard, jagged edges. Before using a Z-pass for a sensitive Defocus or Z-Combine operation, you can run it through the Anti-Aliasing node to soften these jagged edges, which can significantly reduce artifacts in the final composite.
        
    - **Organic (Stylized Pixel Art Upscaling):** While not its intended purpose, it can be used creatively. If you have a very low-resolution, pixelated image (like game sprite art), you can scale it up with Nearest Neighbor interpolation to preserve the sharp pixels. Then, you can use the Anti-Aliasing node to create a smoothed, almost vector-like version of the original pixel art, which can be a unique stylistic choice.
        
    - **Critical Note:** This node is a post-process. It is always better to get good anti-aliasing at render time by using sufficient render samples. This node is a "fix-it-in-post" tool for situations where re-rendering is not an option or for specific data passes like the Z-depth pass. It can sometimes soften texture details as an unwanted side effect.