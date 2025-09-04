- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates a procedural pattern of regular, parallel bands or concentric rings. These patterns can be distorted with built-in noise for more organic effects.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket - Input):** The coordinate space to evaluate the texture in.
        
    - **Type (Property):** The main control for the pattern shape:
        
        - **Bands:** Creates straight, parallel bands.
            
        - **Rings:** Creates concentric rings.
            
    - **Bands/Rings Direction (Property):** Determines the orientation of the pattern (e.g., 'X', 'Y', 'Z' for bands, or 'Spherical' for rings emanating from the origin).
        
    - **Wave Profile (Property):** The shape of the wave's transition:
        
        - **Sine:** A smooth, sinusoidal transition from black to white.
            
        - **Saw:** A sharp, linear ramp from black to white that then drops back to black.
            
    - **Scale (Socket - Input):** Controls the overall size and frequency of the waves.
        
    - **Distortion (Socket - Input):** Adds internal noise to the wave pattern, making the lines wavy and irregular.
        
    - **Detail / Roughness (Sockets - Input):** Control the characteristics of the distortion noise.
        
    - **Color / Factor (Sockets - Output):** The resulting wave pattern, provided as both a color and a grayscale float.
        
- **Practical Application:** The Bands type is perfect for creating the stripes on an animal like a zebra or a tiger.
    
    1. **The Goal:** To create a black and white stripe pattern that realistically conforms to the 3D shape of a zebra model.
        
    2. Start with your zebra mesh. You'll need a coordinate system that flows along the animal's body. A good UV map is a great way to get this.
        
    3. Use the Wave Texture node. Set the Type to 'Bands'.
        
    4. For the Vector input, connect your zebra's UV map. This will make the stripes follow the contours of the body as defined by the UVs.
        
    5. The Factor output is a smooth sine wave. To create sharp stripes, feed this Factor into a Color Ramp node set to 'Constant' interpolation. You can now use the color ramp's handles to precisely control the width and sharpness of the black and white bands.
        
    6. Add a bit of Distortion to the Wave Texture to make the stripes wavy and imperfect, which looks more natural than perfectly straight lines.
        
    7. You can then use this final black and white pattern as a selection mask to drive a Set Material node, applying a "Black_Fur" material to one part and a "White_Fur" material to the other.
        
    8. **The Result:** A fully procedural stripe pattern that intelligently wraps around a complex 3D model.