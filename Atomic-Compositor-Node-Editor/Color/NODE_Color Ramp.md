- **Editor:** Compositor Node Editor
    
- -**Node Group:** Color
    
- **Core Function:** Maps an input grayscale range (from 0.0 black to 1.0 white) to a user-defined color and/or alpha gradient. It is the primary tool for creating masks, colorizing data passes, and art-directing procedural effects.
    
- **Key Properties & Settings:**
    
    - **Factor (Socket):** The grayscale input. Values of 0 are mapped to the leftmost color stop on the ramp, and values of 1 are mapped to the rightmost.
        
    - **Color Ramp (Property):** The gradient widget itself.
        
        - **Color Stops:** You can add, remove, and position multiple color stops along the ramp.
            
        - **Color Picker:** Each stop has its own color and alpha value, which can be set independently.
            
        - **Interpolation Mode:** Controls how the colors blend between stops (e.g., Linear, Ease, B-Spline, Constant). Constant is very useful for creating hard-edged masks.
            
- **Outputs:**
    
    - **Color (Socket):** The final colorized gradient output.
        
    - **Alpha (Socket):** A grayscale output representing only the alpha values from the gradient.
        
- **Practical Application:** The Color Ramp is a "Swiss Army knife." Its power comes from what you feed into its Factor.
    
    - **Molecular (Mask Tightening / Contrast Control):** Its most common use. If you have a soft, grayscale mask (e.g., from a Luma Key or a Texture node), you can feed it into a Color Ramp.
        
        1. Leave the ramp as black-to-white.
            
        2. By sliding the black and white color stops closer to the center, you can precisely control the contrast of the mask, "crushing" the gray values to pure black or white. This is more intuitive and powerful than a Brightness/Contrast node for creating high-quality mattes.
            
    - **Molecular (Colorizing Data):** This is how you visualize data passes.
        
        1. Feed the Mist or Depth pass from a Render Layers node into the Factor.
            
        2. On the ramp, create a gradient from, for example, dark blue (for distant fog) to a light, hazy yellow (for near fog). The node will colorize the raw data, giving you an art-directable atmospheric effect.
            
    - **Organic (Creating a Procedural Vignette):**
        
        1. Use an Image Coordinates node to generate a radial gradient.
            
        2. Feed this gradient into the Factor of a Color Ramp.
            
        3. Set the ramp's gradient to go from black to white.
            
        4. By moving the black color stop and changing the interpolation mode (e.g., to Ease), you can visually and precisely control the size and softness of a perfect, resolution-independent vignette mask.
            
    - **Organic (Stylized "Heat Map" or "Predator Vision" effect):**
        
        1. Take the luminance of your image (e.g., the V channel from a Separate HSV node) and feed it into the Factor.
            
        2. In the Color Ramp, create a complex gradient with multiple stops: Black -> Dark Blue -> Green -> Yellow -> Red -> White.
            
        3. The node will remap the brightness of your scene to this "heat" spectrum, instantly creating a highly stylized look where dark areas are blue, midtones are green/yellow, and the brightest parts are white-hot.