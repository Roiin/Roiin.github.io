**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Maps a grayscale input range (0.0 to 1.0) to a custom, user-defined color or grayscale gradient.

**Key Properties & Settings:**

- **Color (Output):** The final, remapped color or gradient.
    
- **Alpha (Output):** The remapped alpha (transparency) value from the gradient.
    
- **Fac (Input):** The input socket for the grayscale value or texture to be remapped. Input values of 0.0 correspond to the leftmost "stop" on the ramp, and values of 1.0 correspond to the rightmost.
    
- **Color Ramp (Property):** The node's primary interface. It is a gradient editor where you can add, remove, and reposition "stops." Each stop can be assigned a specific color and alpha value, allowing you to build complex custom gradients.
    
- **Interpolation (Property):** Controls how the colors between the stops are blended. Linear provides a smooth, even transition. Constant creates hard-edged, distinct bands, which is perfect for creating masks or cel-shading effects.
    

**Practical Application:**  
This node is one of the most powerful and frequently used tools in procedural texturing, acting as the primary "shaping" tool for the output of noise textures. It is essential for creating the color and texture of **rust**.

The problem is that a raw Noise Texture just outputs a soft, cloudy, black-and-white pattern. It doesn't look like rust. You need to translate this abstract noise into the specific colors and sharp, patchy shapes of real corrosion. The Color Ramp is the definitive solution.

1. Start with a Noise Texture. Connect its Factor output to the Fac input of a Color Ramp node.
    
2. To create a high-contrast mask for the rust, set the Interpolation to Constant. Now, by sliding the black and white stops, you can precisely control the amount and sharpness of the rust patches. This mask will be used to mix between your "Paint" and "Rust" shaders.
    
3. Add a second Color Ramp node. Again, connect the Noise Texture's Factor to its Fac. This ramp will define the rust's color.
    
4. In this second ramp, create a gradient using multiple stops. Start with a dark, desaturated brown on the left, then add a brighter orange, a touch of yellow, and maybe another dark brown. This maps the different brightness values of the original noise to a rich, multi-toned color palette.
    
5. When you use this second ramp to drive the Base Color of your rust shader, the result is a far more believable material. The rust is no longer a single, flat color but has a natural-looking variation in hue and value, all shaped and controlled by the Color Ramps.