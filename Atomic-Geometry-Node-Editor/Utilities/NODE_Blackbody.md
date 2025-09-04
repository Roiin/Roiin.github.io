- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (Color)
    
- **Core Function:** Converts a temperature value (in Kelvin) into a physically accurate color. This follows the black-body radiation spectrum, where lower temperatures are red/orange (like embers) and higher temperatures become yellow, white, and eventually blue (like a hot star).
    
- **Key Properties & Settings:**
    
    - **Temperature (Socket - Input):** A float value representing the temperature in Kelvin. Common values range from ~1500K (red-hot metal) to ~6500K (daylight) to ~10,000K+ (blue-white).
        
    - **Color (Socket - Output):** The resulting RGB color.
        
- **Practical Application:** This node is perfect for adding realistic color variation to effects that involve heat, such as the glowing embers on a magical creature made of lava.
    
    1. **The Goal:** You have a creature whose body is made of cooling lava rock. You want the cracks and crevices to glow with intense heat, and the color of the glow should vary realistically based on how "hot" each part is.
        
    2. First, you create a procedural mask that identifies the deep crevices of your lava creature. The Ambient Occlusion node is perfect for this. It will output a value that is dark in the cracks and bright on the outer surfaces. Invert this so the cracks are white (hot).
        
    3. Use a Map Range node. Map the inverted ambient occlusion value (from 0 to 1) to a Temperature range (e.g., from 1200K for a dull red glow up to 2500K for a bright yellow-orange).
        
    4. Feed this procedural temperature field into the Temperature input of the Blackbody node.
        
    5. The Color output is now a physically accurate color gradient, where the deepest cracks are a bright yellow and the surrounding areas fade to a dull, dark red.
        
    6. Use a Store Named Attribute to save this color as an attribute (e.g., "glow_color"). In your shader, you can plug this attribute directly into the Emission Color and Emission Strength of a Principled BSDF to create a stunning, realistic, and fully procedural glowing lava effect.