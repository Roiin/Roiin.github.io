- **Editor:** Compositor Node Editor
    
- **Node Group:** Input
    
- **Core Function:** Analyzes an input image's properties and outputs its spatial data—such as dimensions, resolution, and transformations—as numerical values for use in other nodes.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The source image from which to extract the data.
        
- **Outputs:**
    
    - **Dimensions (Socket):** Outputs a 2D vector (Width, Height) representing the final size of the image after any transformations (like scaling) have been applied.
        
    - **Resolution (Socket):** Outputs a 2D vector (Width, Height) representing the original, untransformed size of the source image in pixels.
        
    - **Location (Socket):** Outputs a 2D vector representing the X and Y coordinates of the image's center within the composite space.
        
    - **Rotation (Socket):** Outputs the rotation of the image in radians around its center.
        
    - **Scale (Socket):** Outputs a 2D vector representing the X and Y scale applied to the image.
        
- **Practical Application:** This node is the brain for creating effects that automatically adapt to the images they are applied to, making node groups reusable and resolution-independent.
    
    - **Molecular (Aspect-Correct Texture Overlay):** When you overlay a procedural Noise texture, it can appear stretched on a widescreen render.
        
        1. Feed your Render Layers into an Image Info node.
            
        2. Use Separate XYZ on the Resolution output, then a Math (Divide) node to calculate the aspect ratio (Width / Height).
            
        3. When generating your texture, use a Vector Math node to scale the input coordinates by this aspect ratio.
            
        4. The result is a procedural texture that is never stretched, regardless of your final render resolution.
            
    - **Organic (Resolution-Independent Procedural Vignette):** This is a classic and powerful use. Instead of using the simple Vignette node, you can build a more customizable one that never fails.
        
        1. Use the Resolution output of the Image Info node to correctly scale the image's pixel coordinates.
            
        2. Use Vector Math to calculate each pixel's distance from the center of the image, creating a perfect radial gradient.
            
        3. Use a Color Ramp node to precisely control the falloff and size of this gradient.
            
        4. The resulting mask can be used as the Factor in a Mix node to darken the edges of any image. This "organism" will automatically adapt to a 4K widescreen render or a 1080x1080 square image without any manual adjustments.
            
    - **Organic (Automated Watermarking):** You can build a system that automatically places a watermark logo a set number of pixels from the corner. By taking the Resolution (e.g., 1920, 1080), you can use Math nodes to subtract a margin (e.g., 50 pixels) to calculate the precise X and Y coordinates for a Transform node that positions your logo, ensuring it's always perfectly placed no matter how the render resolution changes.