- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (Color)
    
- **Core Function:** Blends two colors (A and B) together using a Factor. It offers a wide variety of blend modes (like Mix, Add, Multiply, Overlay) that determine how the two colors are combined, making it a powerful tool for layering and combining color attributes.
    
- **Key Properties & Settings:**
    
    - **Factor (Socket - Input):** A float that controls the blending. In the default 'Mix' mode, a Factor of 0.0 outputs color A, a Factor of 1.0 outputs color B, and 0.5 is an even mix.
        
    - **A / B (Sockets - Input):** The two color fields to be blended.
        
    - **Blend Mode (Property):** The core control. A dropdown menu offering numerous blend modes familiar from 2D image editors:
        
        - **Mix:** A simple linear interpolation.
            
        - **Add / Multiply:** Brightens or darkens the image.
            
        - **Overlay / Soft Light:** Increases contrast.
            
        - **Color / Hue / Saturation:** Transfers only that specific component from color B to color A.
            
    - **Clamp Factor / Clamp Result (Properties):** Booleans to ensure that the input factor and the final output color remain within the standard 0-1 range.
        
    - **Result (Socket - Output):** The final, blended color.
        
- **Practical Application:** The Mix Color node is essential for layering procedural textures to create complex surface patterns, like adding moss to the crevices of a stone creature.
    
    1. First, you have a base color attribute for your creature, perhaps from a Noise Texture, representing the stone color. This will be color A.
        
    2. You also create a green color for the moss. This will be color B.
        
    3. **The Goal:** You need a mask to control where the moss appears. Moss grows in occluded, creviced areas.
        
    4. The Ambient Occlusion node is perfect for this. It generates a grayscale map that is dark (0.0) in crevices and bright (1.0) on exposed surfaces. Invert this map so the crevices are white. This is your Factor.
        
    5. Use the Mix Color node.
        
        - Connect your stone color to A.
            
        - Connect your moss color to B.
            
        - Connect your inverted ambient occlusion map to the Factor.
            
        - You might set the Blend Mode to 'Overlay' or 'Multiply' for a more natural blend than a simple 'Mix'.
            
    6. **The Result:** The moss color is blended onto the stone color only in the creviced areas defined by your ambient occlusion mask. This creates a realistic, environment-aware texture that automatically adapts to the creature's geometry.