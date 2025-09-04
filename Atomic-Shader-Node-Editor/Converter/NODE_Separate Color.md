**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Deconstructs a color input into its individual component channels based on a chosen color model (RGB, HSV, or HSL).

**Key Properties & Settings:**

- **Mode (Property):** The core control that determines which output channels are available.
    
    - **RGB:** Provides Red, Green, and Blue outputs as separate grayscale values. This is ideal for technical operations or accessing data packed into specific channels.
        
    - **HSV:** Provides Hue, Saturation, and Value outputs as grayscale values. This is more artist-friendly for isolating parts of a texture based on its color, intensity, or brightness.
        
- **Color (Input):** The input socket for the color or texture to be separated.
    
- **Alpha (Output):** If the input color has an alpha channel, its value will be provided here.
    

**Practical Application:**  
This node is essential for isolating specific parts of a texture to be used as a mask or for further manipulation. The HSV mode is particularly powerful for this. Imagine you have an image texture of a rusty metal plate, and you want to make only the orange, rusted areas rougher, leaving the gray, un-rusted metal smoother.

The problem is how to procedurally create a mask that isolates only the orange colors in the texture. The Separate Color node is the perfect solution.

1. Start with your Image Texture of the rusty plate. Connect its Color output to the Base Color of your `Principologin.
    
2. Add a Separate Color node and set its Mode to HSV. Connect the Image Texture's Color output to this node's Color input.
    
3. The node now provides three grayscale outputs. The Hue output will be a map where the color represents the position on the color wheel. The orange/red areas of the rust will have a similar grayscale value in this Hue map.
    
4. Connect the Hue output to a ColorRamp node. By using the color picker in the ColorRamp to sample the grayscale value of the rust's hue, you can create a high-contrast black-and-white mask that isolates only the pixels with that specific hue.
    
5. You can now use this mask to drive the Roughness. For example, use it as the Fac for a Mix node (in Float mode) that blends between a low roughness value (for the metal) and a high roughness value (for the rust). This allows you to precisely target material properties based on the color information in your source texture.