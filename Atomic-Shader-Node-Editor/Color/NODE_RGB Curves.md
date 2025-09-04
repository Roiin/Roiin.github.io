**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Color

**Core Function:** Provides a powerful and precise way to remap the tonal range of a color or texture by using a custom curve, offering far more control than a simple brightness or contrast slider.

**Key Properties & Settings:**

- **Color (Output):** The final, adjusted color result.
    
- **Curve (Property):** The node's primary interface. It's a graph where the horizontal axis (X) represents the input brightness levels (from dark to light) and the vertical axis (Y) represents the output levels. By adding points to the curve and moving them, you can precisely control how specific tonal ranges are remapped.
    
- **Channel (Property):** A dropdown that lets you select which color channel the curve is editing. C (Combined) affects all channels equally for brightness/contrast adjustments. R, G, and B allow you to edit the red, green, or blue channels independently for color correction.
    
- **Color (Input):** The socket for the source color or texture to be adjusted.
    
- **Fac (Input):** A factor to control the overall strength of the node's effect.
    

**Practical Application:**  
This node is the definitive tool for "crushing" or "clamping" the values of a procedural mask to achieve a specific look. Imagine you are using a Noise Texture to create a mask for **rust**. The raw noise has soft, blurry edges, but you want the rust patches to be sharp and well-defined.

The problem is that a Brightness/Contrast node affects the whole tonal range at once. You need a more surgical approach to turn the mid-grays into either pure black or pure white while leaving the extremes untouched. The RGB Curves node is the perfect solution.

1. Take the grayscale Factor output from your Noise Texture.
    
2. Connect it to the Color input of an RGB Curves node.
    
3. In the curve editor, create an "S-curve." Grab the point at the bottom-left (the blacks) and drag it horizontally to the right. This "crushes the blacks," forcing more of the dark-gray values to become pure black.
    
4. Next, grab the point at the top-right (the whites) and drag it horizontally to the left. This "crushes the whites," forcing more of the light-gray values to become pure white.
    
5. The resulting curve will be much steeper in the middle. This dramatically increases the contrast in the mid-tones, effectively turning the soft, blurry noise into a high-contrast mask with sharp, defined edges.
    
6. When you use this adjusted mask to mix your paint and rust shaders, the transition will be crisp and distinct, creating a much more convincing chipped-paint or heavy-corrosion effect.