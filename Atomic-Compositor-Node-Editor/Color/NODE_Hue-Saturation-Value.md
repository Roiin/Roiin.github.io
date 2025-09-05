- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Provides simple, direct slider controls to globally adjust the Hue (the color's tint), Saturation (the color's intensity), and Value (the color's brightness) of an entire image.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Factor (Socket):** A global multiplier for the node's effect. At 0, the node does nothing. At 1, it applies the full effect. This is crucial for masking.
        
    - **Hue (Socket):** Rotates all colors in the image around the color wheel. The default of 0.5 is no change. A value of 0.0 or 1.0 shifts colors by 180 degrees (e.g., blue becomes yellow).
        
    - **Saturation (Socket):** Controls the intensity of all colors. A value of 0.0 removes all color, resulting in a grayscale image. A value of 1.0 is no change. Values greater than 1.0 boost color intensity.
        
    - **Value (Socket):** A multiplier for the image's brightness. A value of 1.0 is no change. Values less than 1.0 darken the image, and values greater than 1.0 brighten it.
        
- **Practical Application:** This is the go-to node for quick, powerful color changes and is a fundamental building block when combined with masks.
    
    - **Molecular (Quick Desaturation):** The simplest and most common way to convert a color image to black and white is to set the Saturation slider to 0.0. You can animate the Saturation value from 1.0 down to 0.0 to create a "color draining away" effect.
        
    - **Molecular (Global Color Shift):** To give an entire scene an alien or surreal look, you can adjust the Hue slider. A small shift can correct a color cast, while a large shift can dramatically change the entire palette, turning a green forest into a purple one, for example.
        
    - **Organic (Secondary Color Correction with Masks):** This is where the node's true power is unlocked. Imagine you want to make a character's red coat more vibrant without affecting their skin tone.
        
        1. Use a Color Key node or Cryptomatte to generate a black-and-white mask of just the red coat.
            
        2. Connect this mask to the Factor input of the Hue/Saturation/Value node.
            
        3. Now, when you increase the Saturation slider, the effect is applied only to the coat (the white areas of the mask), leaving the rest of the image untouched. This "organism" is the foundation of targeted color correction.
            
    - **Organic (Day for Night Color Pass):** After darkening an image to simulate night, you need to tint it blue.
        
        1. Duplicate your image stream. On one branch, use a Hue/Saturation/Value node.
            
        2. Set the Saturation to 0.0 to make it grayscale. Then, use an RGB Curves or Color Balance node to tint this grayscale version blue.
            
        3. Use a Mix node set to Color to combine this blue-tinted version back onto your original darkened footage. This "molecule" applies the color of one image to the brightness of another, creating a very convincing nighttime look.