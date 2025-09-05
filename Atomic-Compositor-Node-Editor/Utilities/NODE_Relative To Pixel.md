- **Editor:** Compositor Node Editor
- **Node Group:** Utilities
    
- **Core Function:** Converts a value expressed as a fraction of the image size into an absolute value measured in pixels.
    
- **Key Properties & Settings:**
    
    - Value ([Socket]): The input float or vector value that is relative to the image size (e.g., 0.5 represents 50%).
        
    - Image ([Socket]): The image input whose resolution serves as the reference for the conversion calculation.
        
    - Data Type ([Property]): Sets whether the node processes a single Float value or a Vector (2D) value.
        
    - Reference Dimension ([Property]): Defines how the relative value is measured against the image's dimensions.
        
        - Per Dimension: Scales the X and Y components of a vector independently against the image's width and height.
            
        - X: Scales the value relative to the image's width only.
            
        - Y: Scales the value relative to the image's height only.
            
        - Greater: Scales the value relative to the larger of the two image dimensions.
            
        - Smaller: Scales the value relative to the smaller of the two image dimensions (often the most predictable for maintaining aspect ratio).
            
        - Diagonal: Scales the value relative to the diagonal length of the image in pixels.
            
    - Value ([Socket]): The output value converted into absolute pixel units.
        
- **Practical Application:**
    
    - **Molecular (Resolution-Independent Blur):** The most critical use of this node is to make effects resolution-independent. A **Blur** node requires a pixel value. A 20px blur looks huge on a 480p image but is negligible on a 4K image. To solve this, create a "molecule" by feeding a **Value** node (e.g., set to 0.01 for a 1% blur) into the **Relative To Pixel** node (set to Smaller), and then pipe the pixel output into the Size input of the **Blur** node. Now, the blur will have the same perceptual softness regardless of the final render resolution.
        
    - **Molecular (Consistent Vignette):** When creating a procedural vignette with a node like **Ellipse Mask**, the size is defined in pixels. To make it robust, use the **Relative To Pixel** node. Feed a **Value** node (with Data Type set to Vector, e.g., [0.4, 0.4]) into it. The output provides resolution-independent Width and Height values for the **Ellipse Mask**, ensuring your vignette frames the shot identically at any output size.
        
    - **Organic (Robust Motion Graphics Templates):** This node is the core "atom" for building professional, reusable motion graphics "organisms." Imagine creating a lower-third template. You need to place a logo, a text box, and background elements at specific screen-relative positions (e.g., 5% from the left edge, 10% from the bottom). By driving the position inputs of **Transform** nodes with values processed through the **Relative To Pixel** node, you create a template that will not break or shift when the user drops it into a 16:9, 4:3, or vertical video project. It makes the entire system predictable and portable.
        
    - **Organic (Procedural Texture Scaling):** In an advanced "organism" for generating a complex procedural effect like a screen-space grid or pattern, you need the pattern's scale to be consistent. By using **Relative To Pixel** to define the core repetition size, you can then use **Math** nodes to derive the correct Scale value for a **Noise Texture** or Thickness for a **Checker Texture**. This ensures that the texture's details don't become too large or small when you change render resolutions, a key step in creating truly professional and shareable procedural assets.