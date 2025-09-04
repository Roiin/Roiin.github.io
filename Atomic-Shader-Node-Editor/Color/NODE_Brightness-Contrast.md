**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Color

**Core Function:** Provides a simple and direct method to adjust the overall brightness and contrast of an input color or texture.

**Key Properties & Settings:**

- **Color (Input):** The input socket for the texture or color to be modified.
    
- **Bright:** Increases or decreases the overall lightness of the input color. Positive values brighten the image, while negative values darken it.
    
- **Contrast:** Increases or decreases the difference between the light and dark areas of the input color. Higher values make brights brighter and darks darker, making details "pop."
    
- **Color (Output):** The final, adjusted color result.
    

**Practical Application:**  
This node is an essential tool for fine-tuning the visual impact of procedural textures. Imagine you have created a procedural **wood grain** texture using a Noise Texture and a ColorRamp. The pattern of the grain is perfect, but the resulting colors look a bit washed out and flat; the dark grain isn't quite dark enough, and the light wood isn't bright enough.

The problem is that re-adjusting the ColorRamp can be finicky and might alter the balance of the pattern you've already perfected. You need a simple way to adjust the overall tonal range after the texture has been generated. The Brightness/Contrast node is the ideal solution.

1. Take the Color output from your ColorRamp that defines the wood grain.
    
2. Instead of plugging it directly into your Principled BSDF, connect it to the Color input of a Brightness/Contrast node first.
    
3. Slightly decrease the Bright value to make the entire wood texture feel richer and less pale.
    
4. Now, increase the Contrast value. This will push the dark grain lines to a deeper brown while simultaneously making the lighter parts of the wood brighter.
    
5. Connect the output of the Brightness/Contrast node to the Base Color of your final shader. The result is the same wood grain pattern, but with a much stronger and more visually appealing tonal range, all achieved with two simple, non-destructive sliders.