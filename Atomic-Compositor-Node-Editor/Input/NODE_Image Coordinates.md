- **Editor:** Compositor Node Editor
    
- **Node Group:** Input
    
- **Core Function:** Generates procedural coordinate systems (visualized as gradients) based on the dimensions and placement of an input image, providing a spatial map of every pixel.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The input image that defines the canvas size for the coordinate generation.
        
- **Outputs:**
    
    - **Uniform (Socket):** Outputs aspect-ratio-independent coordinates, centered at (0,0) in the middle of the image. The values are scaled so that they range from approximately -0.5 to 0.5 along the longest dimension. This is ideal for creating patterns that should not be stretched, like circles.
        
    - **Normalized (Socket):** Outputs coordinates ranging from (0,0) at the bottom-left corner to (1,1) at the top-right. This is equivalent to a UV map for the entire image and is perfect for linear gradients and texture mapping.
        
    - **Pixel (Socket):** Outputs the literal pixel coordinates, with (0.5, 0.5) being the center of the bottom-left pixel. This is useful for creating effects based on the specific pixel grid, like scanlines.
        
- **Practical Application:** This is a cornerstone of proceduralism in the compositor, allowing you to create effects and masks that are independent of image content.
    
    - **Molecular (Perfect Radial Vignette):** The best way to create a fully controllable vignette.
        
        1. Take the Uniform output and feed it into a Vector Math node set to Length. This creates a perfect circular gradient, black at the center and white at the edges, regardless of the image's aspect ratio.
            
        2. Pipe this through a Color Ramp to precisely control the vignette's size, softness, and falloff.
            
        3. Use the result as the Factor in a Mix node to darken or color-tint the edges of your image.
            
    - **Molecular (Linear Wipe Transition):** To create a simple transition between two images.
        
        1. Use the Normalized output.
            
        2. Feed it into a Separate XYZ node and take the X output. This gives you a perfect linear gradient from left (black) to right (white).
            
        3. Use this gradient as the Factor in a Mix node to blend between two input images, creating a smooth wipe. You can animate a Math node or Color Ramp in between to control the transition.
            
    - **Organic (Procedural Scanlines/Grid):** For creating a "screen" effect.
        
        1. Take the Pixel output and Separate XYZ.
            
        2. Feed the Y output into a Math node set to Modulo. A Modulo of 2.0 will create alternating black and white lines (0, 1, 0, 1...). A Modulo of 5.0 will create a black line every 5 pixels.
            
        3. Multiply this result over your main image to create realistic, resolution-dependent scanlines. You can do the same with the X output and combine them to create a perfect grid.