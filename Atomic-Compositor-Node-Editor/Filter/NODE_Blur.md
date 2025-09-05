- **Editor:** Compositor Node Editor
    
- **Node Group:** Filter (Blur)
    
- **Core Function:** Applies a blur to an image, offering a variety of algorithms (filter types) to control the quality and character of the softening effect. It is the most fundamental and versatile blur tool for a wide range of tasks.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be blurred.
        
    - **Size (Socket):** A value input that acts as a multiplier for the X and Y blur radius. Critically, this can be driven by a grayscale mask, allowing you to create a variable blur where the blur amount changes across the image.
        
    - **Filter Type (Property):** The mathematical algorithm used for blurring. Key options include:
        
        - Gaussian: The industry standard for a high-quality, smooth, natural-looking blur. Best for glows and realistic softening. It can be slow.
            
        - Fast Gaussian: An approximation that is much faster but slightly lower in quality. Excellent for previews or less critical blurs.
            
        - Box (called Flat in older versions): The fastest method, but produces a lower-quality, "boxy" look.
            
        - Catmull-Rom: A sharpening blur that attempts to preserve sharp edges while blurring other details. Can be used for specific stylistic effects.
            
    - **X / Y (Properties):** Controls the blur radius in pixels independently for the horizontal and vertical axes. Unequal values will create a streaked, motion-blur-like effect.
        
    - **Relative (Property Checkbox):** When checked, the X/Y values are treated as a percentage of the image dimensions, making the blur effect consistent regardless of final render resolution.
        
    - **Variable Size (Property Checkbox):** Must be enabled to use the Size socket for variable, mask-driven blurring.
        
    - **Extend Bounds (Property Checkbox):** Allows the blur to render outside the original image's boundaries, preventing a hard, clipped edge on heavily blurred elements.
        
- **Practical Application:** A true workhorse for countless effects, from simple softening to complex, mask-driven blurs.
    
    - **Molecular (Creating a Glow):** This is a cornerstone "molecule."
        
        1. Use a Luma Key or RGB Curves to create a mask of only the brightest parts of your image.
            
        2. Feed this highlights-only image into a Blur node (set to Gaussian) with a large radius.
            
        3. Use a Mix node set to Add or Screen to combine this blurry glow back on top of your original image for a soft, blooming effect.
            
    - **Molecular (Anamorphic Streak):** To simulate the horizontal flare of an anamorphic lens:
        
        1. Isolate the highlights of your image.
            
        2. Use a Blur node. Set Y to 0 and give X a large value (e.g., 200).
            
        3. The result is a long horizontal streak that can be Added back over your image.
            
    - **Organic (Mask-Driven Depth of Field):** This is where the Size socket shines. To create an "art-directed" depth of field effect:
        
        1. Create a grayscale mask where you want the image to be sharpest (e.g., a radial gradient centered on a character's face, or a mask that follows a specific object).
            
        2. Invert this mask, so the focus area is black (blur size 0) and the background is white (blur size 1).
            
        3. In the Blur node, enable Variable Size. Connect your inverted mask to the Size input socket.
            
        4. Set the X and Y values to the maximum blur amount you want. The mask will now control the blur, applying the full blur radius in the white areas and no blur in the black areas, creating a custom, controllable focus effect without needing a Z-pass.