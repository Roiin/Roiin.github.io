- **Editor:** Compositor Node Editor
- **Node Group:** Color
    
- **Core Function:** A technical utility node that converts the alpha channel of an image between two formats: **Premultiplied** (Blender's internal standard) and **Straight** (used by some external software and required for certain operations).
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Mapping (Property):** The conversion direction.
        
        - To Premultiplied: Converts an image with straight alpha into Blender's native format.
            
        - To Straight: Converts a premultiplied alpha image out of Blender's native format.
            
- **Practical Application:** This node acts like a "translator" for the alpha channel. While Blender handles most conversions automatically on input/output, you sometimes need to manually manage the format in the middle of a node tree to ensure certain "atoms" work correctly.
    
    - **Important Context:**
        
        - **Premultiplied Alpha (Blender's Default):** The RGB color values of a pixel have been multiplied by its alpha value. This is the industry standard for rendering and compositing as it leads to more accurate results with operations like blurring and blending.
            
        - **Straight Alpha (Unpremultiplied):** The RGB color values are stored "pure," independent of the alpha channel.
            
    - **Organic (Correct Color Correction):** This is the most common and critical use case. Applying color correction (like RGB Curves or Color Balance) to a premultiplied image can lead to a dark or black "fringe" around the edges of transparent objects. The color correction is incorrectly applied to the black background that is "pre-multiplied" into the RGB channels. The correct "molecule" for this is:
        
        1. Start with your render (which is Premultiplied).
            
        2. Use Alpha Convert set to To Straight. This "un-multiplies" the alpha, restoring the pure edge colors.
            
        3. Now, perform your RGB Curves or Color Balance operation. The correction will be applied cleanly to the true colors.
            
        4. Finally, use another Alpha Convert node set back To Premultiplied to return the image to Blender's standard format before continuing your composite (e.g., before an Alpha Over node). This is called the "Unpremult-Remult" workflow.
            
    - **Organic (Integrating External Elements):** If you receive an image file from another software (like a motion graphics package) that was explicitly saved with Straight alpha, Blender might misinterpret it. While the Image node has settings for this, if you need to be certain, you can place an Alpha Convert node set to To Premultiplied directly after the Image node to ensure it is correctly formatted for all subsequent operations in Blender.