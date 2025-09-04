**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a uniform random value (a color or a grayscale factor) for any given input coordinate, creating a static-like or cellular random pattern.

**Key Properties & Settings:**

- **Value (Output):** Provides a single, random grayscale value between 0.0 and 1.0.
    
- **Color (Output):** Provides a single, random RGB color where each channel is an independent random value.
    
- **Dimensions (Property):** Determines which inputs are used as the "seed" for the random number generation. 3D is the most common for surfaces, using the Vector input.
    
- **Vector / W (Inputs):** The seed inputs. Unlike a Noise Texture which creates a smooth gradient, the White Noise node will output the exact same random value for any given unique input seed.
    

**Practical Application:**  
This node's power is unlocked when you feed it a discrete, non-continuous coordinate system. It is the perfect tool for creating materials like a mosaic floor or stylized terrazzo, where each individual tile or stone chip needs a unique, random color.

The problem is how to assign a different color to each "tile" in a procedural grid. A Voronoi texture can create random colors, but the cells are often organic and rounded. To create a grid of square tiles, you need a different approach. The White Noise Texture is the solution when combined with a Snap operation.

1. Start by taking your object's Texture Coordinate.
    
2. Use a Vector Math node set to the Snap operation. This function takes the continuous texture coordinates and rounds them down to the nearest grid increment (e.g., rounds 0.1, 0.2, 0.3 all down to 0). This effectively creates a grid of cells, and every point inside one of these cells now shares the exact same coordinate value.
    
3. Feed the output of this Snap node into the Vector input of the White Noise Texture node.
    
4. Since every point within a single "tile" is now providing the identical seed coordinate, the White Noise node will output the same random color for that entire tile.
    
5. Connect the Color output of the White Noise node to your Principled BSDF's Base Color.
    
6. The result is a perfect grid of square tiles, where each tile has its own distinct, randomly generated color, all controlled by a single, efficient material. This is a fundamental technique for creating procedural tiled patterns.