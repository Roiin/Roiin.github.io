- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (Color)
    
- **Core Function:** Provides a Bézier curve widget to precisely remap the tonal range of an input color or float value. It allows for non-linear adjustments, offering much finer control than a Color Ramp.
    
- **Key Properties & Settings:**
    
    - **Factor (Socket - Input):** Controls the overall influence of the node. A factor of 0 passes the input color through unchanged.
        
    - **Color (Socket - Input):** The source color or float value to be adjusted.
        
    - **Curve Widget (Property):** The main interface. The X-axis represents the input brightness levels (0 to 1), and the Y-axis represents the output brightness levels. By adding and moving points on the curve, you can selectively brighten, darken, or add contrast.
        
    - **Channel (Property):** A dropdown to select which channel the curve widget is currently editing:
        
        - **C:** Combined (adjusts R, G, and B channels together).
            
        - **R, G, B:** Adjusts the individual Red, Green, or Blue channels.
            
    - **Color (Socket - Output):** The final, adjusted color.
        
- **Practical Application:** This node is perfect for fine-tuning procedural textures to achieve a specific look, like creating the subtle color variations and harsh highlights on a creature's metallic scales.
    
    1. Start with a Noise Texture to create a base pattern for the scales. The Factor output is a grayscale gradient.
        
    2. **The Goal:** You want to transform this smooth noise into a pattern that looks like hammered or tarnished metal, which has sharp highlights and deep shadows.
        
    3. Feed the Factor from the Noise Texture into the Color input of the RGB Curves node.
        
    4. **The Curve:** In the curve widget, create an "S"-shaped curve.
        
        - Drag the point at the bottom-left corner to the right. This will "crush the blacks," making the dark areas of the noise even darker and flatter.
            
        - Drag the point at the top-right corner to the left. This will "blow out the whites," making the bright areas of the noise even brighter and flatter.
            
        - Add a point in the middle and increase the slope of the curve. This increases the contrast in the mid-tones.
            
    5. The output of the RGB Curves node is now a high-contrast grayscale map. You can use this to drive the Metallic and Roughness inputs of a Principled BSDF shader, or even as a bump map.
        
    6. **The Result:** The smooth, generic noise has been transformed into a pattern with the harsh, high-contrast look of worn metal. The RGB Curves node provided the precise, non-linear control needed to achieve this specific artistic effect.