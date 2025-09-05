- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Mix)
    
- **Core Function:** Blends two images (A and B) together using a variety of mathematical blend modes and a factor to control the strength of the mix. It is one of the most fundamental and frequently used nodes for combining, layering, and manipulating image data.
    
- **Key Properties & Settings:**
    
    - **Data Type (Property):** Set to Color for image manipulation.
        
    - **Mix (Blend Mode) (Property):** A dropdown menu with numerous blend modes, each performing a different mathematical operation. Key modes include:
        
        - Mix: A simple linear interpolation (like opacity).
            
        - Add/Screen: Brightening modes, excellent for adding glows, flares, and light effects.
            
        - Multiply/Darken: Darkening modes, useful for adding shadows or grime.
            
        - Overlay/Soft Light: Contrast-enhancing modes, perfect for adding textures or applying color tints.
            
        - Color/Hue/Saturation: Component modes that transfer only that specific attribute from one image to another.
            
    - **Factor (Socket):** Controls the strength of the blend. At 0, only input A is shown. At 1, the full effect of the blend mode with input B is applied.
        
    - **A (Socket):** The base image, or "bottom layer."
        
    - **B (Socket):** The image being blended on top, or "top layer."
        
    - **Clamp Result (Property Checkbox):** Prevents the output from having color values outside the normal 0-1 range. Essential for avoiding artifacts when using strong Add or Multiply operations.
        
- **Practical Application:** This node is the atomic glue of compositing. It's how you combine nearly everything to achieve artistic effects.
    
    - **Molecular (Color Grading with Tints):** To give your image a warm, "golden hour" feel:
        
        1. Connect your render to input A.
            
        2. Connect a solid orange color from an RGB node to input B.
            
        3. Set the blend mode to Overlay or Soft Light.
            
        4. Adjust the Factor to a low value (e.g., 0.1-0.3). The orange color will tint your image in a pleasing, contrast-aware way. Use a blue color for a "moonlit" feel.
            
    - **Molecular (Adding Textures):** To add film grain or a grunge texture to a clean render:
        
        1. Connect your render to input A.
            
        2. Connect your grain/grunge texture (loaded with an Image node) to input B.
            
        3. Set the blend mode to Overlay. The gray values of the texture will non-destructively add detail and imperfection.
            
    - **Organic (Screen Glow / Light Bloom):** A common way to create a light bloom effect.
        
        1. Duplicate your image stream. On one branch, use an RGB Curves or Luma Key node to isolate only the brightest parts of the image (like lightbulbs or reflections).
            
        2. Blur this "highlights only" image heavily.
            
        3. Use a Mix node set to Add or Screen. Connect the original image to A and the blurred highlights to B. The result is a soft, realistic bloom of light around the brightest areas.
            
    - **Organic (Applying a Mask):** This is a fundamental "molecule" for targeted adjustments.
        
        1. You have your original image and a color-corrected version.
            
        2. You also have a black-and-white mask (e.g., from a Mask node or Cryptomatte) that defines where you want the correction to happen.
            
        3. Connect the original image to input A of a Mix node.
            
        4. Connect the color-corrected version to input B.
            
        5. Connect the black-and-white mask to the Factor socket.
            
        6. The result is an image where the color correction is applied only in the white areas of the mask, perfectly blending the two versions.