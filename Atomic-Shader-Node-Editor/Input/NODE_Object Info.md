**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides object-specific information, such as a unique random value, allowing a single material to appear differently across multiple objects that share it.

**Key Properties & Settings:**

- **Random (Output):** The most powerful output. It generates a unique grayscale value (from 0 to 1) for each individual object in the scene.
    
- **Location (Output):** Outputs the world-space coordinates of the object's origin point. This can be used to drive effects that change based on an object's position.
    
- **Object Index (Output):** Outputs the integer value set in the object's "Pass Index" field, allowing for manual, artist-driven variation instead of random chance.
    
- **Color (Output):** Outputs the color swatch set in the object's "Viewport Display" panel, providing another direct way to control a material's appearance on a per-object basis.
    

**Practical Application:**  
This node is essential for breaking up repetition when a single material is used on many objects. Imagine creating a floor made of dozens of individual **wood grain** planks. If they all share the same material, the wood grain pattern and color will be identical on every single plank, looking artificial and computer-generated.

The problem is how to make each plank unique without creating dozens of separate materials. The Random output of the Object Info node is the solution.

1. Create your base wood material, likely using a Noise Texture and a ColorRamp to define the grain's color.
    
2. To vary the color of each plank, connect the Random output to the Fac input of a new ColorRamp. This ColorRamp can contain a range of different wood tones. When plugged into the Base Color of the Principled BSDF, each plank will be assigned a random color from that gradient.
    
3. To vary the grain pattern, use a Vector Math node to add the Random output to the texture coordinates feeding your Noise Texture. This will shift or "offset" the texture by a different amount for each plank, ensuring no two grain patterns are perfectly aligned.
    
4. By combining these techniques, a single, efficient material can generate a floor of seemingly infinite variation, with each plank having a unique color and grain pattern, achieving a natural, realistic look.