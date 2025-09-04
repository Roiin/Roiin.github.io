**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Simulates a medium that absorbs or filters light, causing it to lose intensity and change color as it travels through the volume.

**Key Properties & Settings:**

- **Volume (Output):** The shader's only output. It must be connected to the Volume input of a Material Output or World Output node.
    
- **Density (Input):** Controls the strength or thickness of the absorbing medium. A higher value will absorb light more quickly over a shorter distance, making the volume appear darker and more opaque.
    
- **Color (Input):** Defines which wavelengths of light are allowed to pass through. A pure white color absorbs all light equally (making the volume gray), while a colored input will absorb the complementary colors. For example, a blue color input will absorb red and green light, allowing blue light to pass through most easily.
    

**Practical Application:**  
This node is essential for creating realistic colored transparent materials like deep water, gemstones, or colored glass. Its key feature is that the color becomes more intense as the object's volume gets thicker. It's perfect for creating deep, blue glacial **ice**.

The problem is that if you just set the Color on a Glass BSDF to blue, the material has a uniform blue tint, regardless of thickness. A thin sliver of ice will look just as blue as a massive block, which is physically incorrect. You need the color to be dependent on volume. Volume Absorption is the solution.

1. For the material's surface, use a Glass BSDF node. Set its Color to pure white and its IOR to 1.31 (the correct value for ice).
    
2. Add a Volume Absorption node. This will control the material's interior.
    
3. Set the Color of the Volume Absorption node to a light, slightly desaturated blue.
    
4. Set the Density to a value that suits the scale of your object. A lower density means light can travel further before being fully absorbed.
    
5. Connect the Glass BSDF to the Surface input of the Material Output node.
    
6. Connect the Volume Absorption node to the Volume input of the Material Output node.
    
7. The result is a physically accurate material. Thin sections of the object will appear almost perfectly clear, while the thicker, core sections will become a deep, rich blue as more and more non-blue light is absorbed over the longer distance. This correctly simulates the volumetric color of deep glacial ice.