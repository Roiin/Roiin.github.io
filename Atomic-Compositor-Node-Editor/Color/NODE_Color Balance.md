- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Provides a powerful and precise method for adjusting the color and tonal range of an image by giving independent control over its shadows, midtones, and highlights. It is the core tool for cinematic color grading and correcting color casts.
    
- **Key Properties & Settings:**
    
    - **Correction Formula (Property):** Lets you choose between Lift/Gamma/Gain (a common, artist-friendly model) and Offset/Power/Slope (the ASC-CDL standardized formula used in the film industry for interoperability).
        
    - **Factor (Socket):** Controls the overall influence of the node's adjustments.
        
    - **Image (Socket):** The standard color input.
        
- **Lift / Gamma / Gain Controls:**
    
    - **Lift (Color Wheel):** Adjusts the darkest parts of the image (the shadows). Pushing this towards blue will make only the shadows in your image blue, without affecting the highlights.
        
    - **Gamma (Color Wheel):** Adjusts the middle gray tones of the image (the midtones). This has the broadest effect on the image's overall color.
        
    - **Gain (Color Wheel):** Adjusts the brightest parts of the image (the highlights). Pushing this towards yellow will tint bright lights and reflections yellow, leaving shadows unaffected.
        
- **Practical Application:** This is the node you use to define the mood and style of your final image.
    
    - **Molecular (Correcting Color Cast):** If your render has an unwanted green tint, you can go to the Gamma wheel (which affects the whole image) and drag the color picker slightly towards magenta (the opposite of green) until the image looks neutral.
        
    - **Molecular (Blockbuster "Orange & Teal" Look):** A very popular cinematic color grade.
        
        1. In the Gain wheel, push the color slightly towards a warm orange or yellow. This makes highlights like skin tones and explosions feel warmer and more vibrant.
            
        2. In the Lift wheel, push the color slightly towards a cool teal or cyan. This makes shadows feel colder and deeper, creating a strong color contrast that is visually appealing.
            
        3. Adjust the Gamma to balance the overall look.
            
    - **Organic (Day for Night Transformation):** To make footage shot during the day look like it was filmed at night:
        
        1. First, use a Brightness/Contrast or RGB Curves node to significantly darken the image.
            
        2. Then, use a Color Balance node. Heavily push the Lift and Gamma towards a deep, desaturated blue or cyan to simulate moonlight.
            
        3. Slightly push the Gain towards a very pale yellow or orange to make artificial lights (like lamps or headlights) feel warmer in contrast to the cool moonlight.
            
    - **Organic (Targeted Adjustments with Masks):** The true power comes from combining this node with masks.
        
        1. Use a Luma Key node to create a mask of just the highlights of your image.
            
        2. Use this mask as the Factor for a Color Balance node.
            
        3. Now, any adjustments you make in this Color Balance node will only affect the highlights, giving you an extreme level of precision. You could, for example, make only the brightest specular reflections on a car have a cool blue tint, creating a stylized, high-tech look.