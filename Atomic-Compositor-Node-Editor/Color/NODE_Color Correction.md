- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Provides a highly detailed interface for adjusting saturation, contrast, gamma, gain, and lift, with the unique ability to apply these corrections independently to the image's shadows, midtones, and highlights.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Mask (Socket):** A factor input that allows a grayscale mask to control where on the image the correction is applied.
        
    - **Master Controls:**
        
        - **Saturation:** Adjusts the color intensity of the entire image.
            
        - **Contrast:** Adjusts the tonal difference of the entire image.
            
        - **Gamma/Gain/Lift:** Sliders for adjusting midtones, highlights, and shadows globally.
            
    - **Highlights / Midtones / Shadows Sections:**
        
        - Each of these three sections contains its own independent set of Saturation, Contrast, Gamma, Gain, and Lift sliders. This is the node's key feature.
            
    - **Tonal Range Controls:**
        
        - **Midtones Start/End:** Sliders that define the brightness range that the node considers to be "midtones." This allows you to precisely define what parts of your image are affected by the Midtones sliders versus the Shadows/Highlights sliders.
            
- **Practical Application:** This node is a "one-stop-shop" for advanced color grading, allowing you to perform operations that would otherwise require multiple nodes and complex masks.
    
    - **Molecular (Targeted Saturation Boost):** A common technique to make an image "pop" without looking oversaturated is to boost color in the midtones while slightly desaturating the shadows and highlights.
        
        1. In the Midtones section, slightly increase the Saturation slider.
            
        2. In the Shadows and Highlights sections, slightly decrease the Saturation sliders.
            
        3. The result is a rich, vibrant image that avoids the unnatural, "bleeding" colors that can occur in very dark or very bright areas with a simple global saturation boost.
            
    - **Molecular (Crushing/Lifting Blacks):** To achieve a faded, "vintage film" look:
        
        1. Go to the Shadows section.
            
        2. Slightly increase the Lift slider. This will raise the darkest parts of the image, making them a dark gray instead of pure black.
            
        3. Slightly decrease the Saturation in the Shadows section as well to complete the washed-out effect.
            
    - **Organic (Skintone Protection):** This node is excellent for protecting delicate skin tones during a heavy color grade.
        
        1. Use a Color Key or Cryptomatte node to create a mask of the character's skin.
            
        2. Feed this mask into the Mask input of the Color Correction node.
            
        3. Now, you can apply a heavy "Orange & Teal" grade to the entire image using a Color Balance node before this one. The Color Correction node, guided by the mask, can then be used to reduce the saturation and contrast only on the skin, making it look natural while the rest of the scene remains heavily stylized.
            
    - **Organic (Enhancing Fire/Explosions):** To make an explosion feel more powerful:
        
        1. In the Highlights section, significantly increase the Saturation and Gain.
            
        2. In the Midtones section, moderately increase the Saturation and Contrast.
            
        3. In the Shadows section, slightly decrease the Saturation to keep the smoke from looking too colorful.
            
        4. This tiered approach makes the brightest parts of the fire intensely vibrant and hot-looking, while the midtones carry the body of the color, and the shadows remain as dark smoke, creating a much more dynamic and believable effect than a single global adjustment.