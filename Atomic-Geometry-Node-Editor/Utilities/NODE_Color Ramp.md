- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (Color)
    
- **Core Function:** Remaps a grayscale input Factor (ranging from 0.0 to 1.0) to a custom color gradient. It is the primary tool for visually art-directing the output of procedural textures and other float values.
    
- **Key Properties & Settings:**
    
    - **Factor (Socket - Input):** A float field, typically from a procedural texture or a distance calculation. Values of 0 are mapped to the leftmost color stop on the ramp, and values of 1 are mapped to the rightmost.
        
    - **Color Ramp (Widget):** The interactive gradient editor on the node itself. You can add, delete, and move color stops, change their color and alpha, and set the interpolation mode (e.g., Linear, Ease, Constant) between them.
        
    - **Color (Socket - Output):** The resulting color after remapping the Factor.
        
    - **Alpha (Socket - Output):** The resulting alpha (transparency) value after remapping.
        
- **Practical Application:** The Color Ramp is essential for shaping the output of procedural textures to create natural patterns, like the spots on a leopard.
    
    1. Start with your leopard model.
        
    2. **The Goal:** To create the characteristic dark, ring-like spots with a lighter brown center.
        
    3. Use a Voronoi Texture. The Distance output gives you a series of circular black-to-white gradients, one for each "spot".
        
    4. **The Problem:** This simple gradient doesn't look like a leopard spot.
        
    5. **The Solution:** Feed this Distance gradient into the Factor of a Color Ramp node.
        
        - Set the color ramp's interpolation to 'Ease' or 'B-Spline' for smooth transitions.
            
        - Add four color stops:
            
            1. At position 0.0: A dark brown/black color (the outer ring of the spot).
                
            2. At position ~0.4: Another dark brown/black color (this creates the thick ring).
                
            3. At position ~0.5: A lighter, tan color (the center of the spot).
                
            4. At position 1.0: The base yellow/orange fur color (the area outside the spot).
                
    6. The Color Ramp has now remapped the simple circular gradient into a complex, multi-colored pattern that perfectly mimics the look of a leopard's rosette. You can now store this color as an attribute and use it to drive the Base Color in your fur shader, creating a fully procedural and highly realistic coat pattern.