**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Converts a color input into a single grayscale (black-and-white) value based on its perceived luminance.

**Key Properties & Settings:**

- **Val (Output):** The final, grayscale numerical value.
    
- **Color (Input):** The socket for the source color or texture to be converted.
    

**Practical Application:**  
This node provides a simple and explicit way to convert a color texture into a grayscale map suitable for controlling non-color attributes like roughness or bump height. While Blender often performs this conversion automatically when you connect a yellow socket to a gray one, using the RGB to BW node makes the node tree's logic clearer and more readable.

Imagine you have a single color image texture of dirty, stained concrete. This image contains both the color information and, implicitly, the roughness information (the darker, wet-looking stains should be shinier than the dry, light concrete).

The problem is you need to extract the brightness information from the color image to control the Roughness input of your shader. The RGB to BW node is the most explicit way to do this.

1. Start with your Image Texture of the stained concrete. Connect its Color output to the Base Color of your Principled BSDF.
    
2. Add an RGB to BW node. Connect the Color output of the Image Texture to this node's Color input.
    
3. The Val output of the node now contains a grayscale representation of your texture. Darker stains are now black/dark gray, and the lighter concrete is white/light gray.
    
4. Since you want the dark, wet stains to be less rough (shinier), you'll need to invert this logic. A simple way is to pass the Val output through a ColorRamp and swap the black and white handles.
    
5. Connect the final result to the Roughness input of your Principled BSDF.
    
6. By explicitly converting the color image to a grayscale value, you can then easily manipulate it to drive other physical properties of the material, ensuring the color and roughness are perfectly synchronized.