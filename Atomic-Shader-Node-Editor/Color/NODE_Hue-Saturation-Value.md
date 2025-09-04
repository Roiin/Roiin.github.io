**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Color

**Core Function:** Provides artistic control to adjust the hue (the color itself), saturation (the intensity of the color), and value (the brightness) of an input color or texture.

**Key Properties & Settings:**

- **Color (Output):** The final, adjusted color result.
    
- **Hue (Input):** Rotates the colors around the color wheel. The default of 0.5 makes no change. Values from 0.5 to 1.0 shift colors towards red/magenta, while values from 0.5 to 0 shift them towards green/cyan.
    
- **Saturation (Input):** Controls the intensity of the color. A value of 1.0 makes no change. A value of 0 removes all color, resulting in a grayscale image. Values greater than 1.0 make the colors more vibrant and intense.
    
- **Value (Input):** Controls the brightness of the color. A value of 1.0 makes no change. A value of 0 results in black, while values greater than 1.0 increase the brightness.
    
- **Fac (Input):** A factor to control the overall strength of the node's effect. A value of 0 has no effect, while a value of 1.0 applies the full adjustment.
    

**Practical Application:**  
This node is essential for creating variations and adding artistic flair to existing textures. Imagine you have a single, high-quality image texture of green leaves, but you need to create an entire forest with a natural variety of colors. Some leaves should be a vibrant spring green, others a dry yellow-green, and some even a reddish autumn hue.

The problem is that sourcing or creating dozens of unique leaf textures is time-consuming. You need a way to procedurally generate this variation from a single source image. The Hue/Saturation/Value node is the perfect solution.

1. Start with your Image Texture of the green leaf.
    
2. To create random color variations, add an Object Info node and connect its Random output to the Hue input of a Hue/Saturation/Value node. This will give every single leaf object a completely random hue.
    
3. The result will be too chaotic (a rainbow of leaves), so you need to constrain it. Insert a Map Range node between the Object Info and the Hue/Saturation nodes. Set the From Min/Max to 0 and 1, and the To Min/Max to a narrow range around 0.5 (e.g., 0.45 to 0.55). Now, the hue will only shift slightly, creating a natural range of greens, yellows, and oranges.
    
4. You can use the same technique with the Saturation and Value inputs to create leaves that are more or less vibrant and bright.
    
5. By using a single leaf texture and modifying it with the HSV node driven by a random input, you can generate a forest of seemingly infinite, natural color variation from just one source image.