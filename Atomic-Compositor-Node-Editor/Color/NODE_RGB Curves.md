- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Provides an advanced, curve-based interface for remapping the tonal range of an image. It offers ultimate control over brightness, contrast, and color balance by allowing you to directly manipulate the relationship between input and output values for the composite channel or for the Red, Green, and Blue channels independently.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Factor (Socket):** Controls the overall influence of the node's adjustments.
        
    - **Black/White Level (Property):** Color pickers that let you define which color in the input image should become pure black and which should become pure white, automatically stretching the tonal range to fit.
        
    - **Channel (Property):** A dropdown to select which curve you are editing: C (Combined RGB), R (Red), G (Green), or B (Blue).
        
    - **Curve (Property):** The main interface.
        
        - The **X-axis** represents the input brightness levels (from black on the left to white on the right).
            
        - The **Y-axis** represents the output brightness levels (from black at the bottom to white at the top).
            
        - The default straight 45-degree line means no change.
            
- **Practical Application:** This node can replicate the function of Brightness/Contrast, Invert, and Gamma nodes, but with far greater precision and artistic control.
    
    - **Molecular (S-Curve for Contrast):** The most common use. By creating a gentle "S" shape in the C (Combined) curve, you are making the darks darker and the brights brighter. This is the classic way to add cinematic contrast to a flat-looking render, offering much more nuance than a simple Contrast slider.
        
    - **Molecular (Faded Film Look):** To create a "crushed blacks" or vintage look:
        
        1. In the C curve, grab the bottom-left point (which represents pure black).
            
        2. Drag this point straight up.
            
        3. This remaps the darkest parts of your image to a gray value instead of black, instantly giving it a soft, faded, and non-digital appearance. You can do the opposite (drag the top-right point down) to "crush the whites."
            
    - **Organic (Color Channel Bleeding):** A powerful technique for unique color grades.
        
        1. Go to the B (Blue) channel's curve.
            
        2. Create a subtle "S" curve. This will add blue to the highlights and remove it from the shadows (effectively adding yellow), creating an instant "cool highlights, warm shadows" effect with a single curve.
            
        3. By manipulating the individual R, G, and B curves, you can achieve any look that the Color Balance node can, but with full control over how the effect is distributed across the entire tonal range.
            
    - **Organic (Luma Keying):** This node can act as a powerful and flexible keyer.
        
        1. Create a curve in the C channel that is flat at the bottom (black), then spikes up to the top (white) in the middle, and then is flat at the bottom again.
            
        2. This "molecule" creates a black-and-white mask that isolates a specific brightness range (the mid-tones). You can adjust the curve handles to precisely control the range and softness of this luma key, which can then be used as a Factor for other effects. This is often more intuitive and powerful than a dedicated Luma Key node.