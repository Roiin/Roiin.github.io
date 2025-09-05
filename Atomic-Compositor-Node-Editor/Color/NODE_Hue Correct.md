- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Provides a curve-based interface to precisely adjust the Hue, Saturation, or Value (Brightness) of specific color ranges within an image. It allows you to target and change, for example, only the greens or only the reds with pinpoint accuracy.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Factor (Socket):** Controls the overall influence of the node's adjustments.
        
    - **Level (Property):** A dropdown to select which attribute the curve will control: H (Hue), S (Saturation), or V (Value).
        
    - **Curve (Property):** The main interface.
        
        - The **X-axis** of the curve represents the entire hue spectrum of the input image (Red -> Yellow -> Green -> Cyan -> Blue -> Magenta -> Red).
            
        - The **Y-axis** represents the amount of change applied to the selected Level. A point at the center line means no change. Moving a point up increases the H/S/V for that hue; moving it down decreases it.
            
- **Practical Application:** This is the ultimate node for "secondary color correction"—the art of adjusting specific colors in a scene without affecting others.
    
    - **Molecular (Making Foliage More Lush):** If the green trees and grass in your render look a bit dull or yellowish:
        
        1. Set the Level to S (Saturation).
            
        2. In the Curve widget, find the green-yellow section on the X-axis.
            
        3. Click to add a control point in that area and drag it upwards.
            
        4. This will increase the saturation of only the green and yellow pixels in your image, making the foliage more vibrant without affecting skin tones or the blue sky.
            
    - **Molecular (Fixing "Digital" Blue Skies):** Sometimes a rendered sky can look like an unnaturally pure blue.
        
        1. Set the Level to H (Hue).
            
        2. Find the blue section of the curve.
            
        3. Drag the control point in that area slightly downwards (towards cyan) or upwards (towards magenta/purple).
            
        4. This shifts the hue of the sky to a more realistic cyan or a more stylized purple, giving it more character.
            
    - **Organic (Color Isolation / "Sin City" Effect):** A classic and powerful use. To make an entire image black and white except for a single red dress:
        
        1. Set the Level to S (Saturation).
            
        2. Click and drag the entire curve all the way to the bottom. This desaturates the whole image, making it black and white.
            
        3. Now, add a control point in the red/magenta area of the curve.
            
        4. Drag this single point back up to the center line (or even higher).
            
        5. The result is an image where only the red hues retain their color, while everything else is grayscale.
            
    - **Organic (Perfecting Green Screen Keys):** After using a Keying node on green screen footage, you might have some green "spill" light reflecting on the actor. The Hue Correct node is perfect for cleaning this up.
        
        1. After keying, set the Level to S (Saturation).
            
        2. Find the green part of the curve and drag it down significantly.
            
        3. This specifically desaturates any remaining green pixels on your actor (e.g., in their hair or on the edges of their clothing) without affecting their skin tone, leading to a much cleaner and more believable composite.