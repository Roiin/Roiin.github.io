- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (Color)
    
- **Core Function:** Deconstructs a color input into its separate, individual channel outputs (like Red, Green, and Blue, or Hue, Saturation, and Value).
    
- **Key Properties & Settings:**
    
    - **Mode (Property):** The color model to use for separating the channels:
        
        - **RGB:** Outputs separate Red, Green, and Blue channels.
            
        - **HSV:** Outputs separate Hue, Saturation, and Value channels.
            
        - **HSL:** Similar to HSV, but outputs Lightness.
            
    - **Color (Socket - Input):** The source color to be deconstructed.
        
    - **Channel Outputs (Sockets):** Three float sockets that change based on the selected Mode (e.g., R, G, B), each providing a grayscale representation of that channel's value.
        
    - **Alpha (Socket - Output):** The transparency value of the input color.
        
- **Practical Application:** The 'HSV' mode is incredibly useful for creating effects based on a specific color. Imagine you have a creature with a complex, multi-colored skin pattern (e.g., a parrot), and you want to instance tiny, reflective feathers only on the red parts of its plumage.
    
    1. First, you have your parrot's color pattern stored as a vertex color attribute.
        
    2. **The Goal:** To create a selection mask that is True only for the red areas.
        
    3. Use the Separate Color node set to 'HSV' mode. Feed your parrot's color attribute into the Color input.
        
    4. The Hue output is a grayscale value representing the color's position on the color wheel. Red colors will have a specific, narrow range of hue values (e.g., from 0.0 to 0.1 and 0.9 to 1.0, since it wraps around).
        
    5. Use a Compare node (or two, combined with a Boolean Math 'Or' node) to check if the Hue value falls within this "red" range.
        
    6. The output of this comparison is now a perfect Boolean selection for all the red parts of the parrot's plumage.
        
    7. You can now feed this selection into a Distribute Points on Faces node to scatter your reflective feather instances, ensuring they only appear on the red feathers, creating a highly specific and realistic detail.