- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** Applies a variety of classic, kernel-based image processing filters to achieve effects like sharpening, simple blurring, edge detection, and embossing.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Factor (Socket):** Controls the blend between the original image and the filtered result.
        
    - **Type (Property):** A dropdown menu to select the filter kernel:
        
        - Soften: A simple, uniform blur.
            
        - Sharpen (Box, Diamond): Increases local contrast at edges to make the image appear sharper. Diamond is generally a subtler and higher-quality version.
            
        - Laplace, Sobel, Prewitt, Kirsch: A family of edge-detection filters. They output a grayscale image that highlights the edges and contours of the input. They vary slightly in their sensitivity and the quality of the lines they produce (Kirsch is often smoothest).
            
        - Shadow: Creates a simple "emboss" or "relief" effect by shifting the image and subtracting it from the original, highlighting edges with light and shadow.
            
- **Practical Application:** While many of these filters are simple "atoms," they are incredibly powerful as building blocks for generating complex masks and stylized effects.
    
    - **Molecular (Non-Destructive Sharpening):** Simply applying a sharpen filter can look harsh. A more professional "molecule" is to apply it subtly:
        
        1. Feed your image into a Filter node set to Sharpen.
            
        2. Use a Mix node. Connect your original image to the top socket and the sharpened version to the bottom socket.
            
        3. Adjust the Factor of the Mix node (e.g., to 0.25). This allows you to blend in just the right amount of sharpening for a crisp but not overly digital look.
            
    - **Molecular (Stylized Outlines):** To create a simple outline effect for motion graphics or text:
        
        1. Use one of the edge-detection filters like Sobel or Kirsch on your image or its alpha channel. This creates a black-and-white line drawing.
            
        2. You can then use a Mix node set to Screen or Add to overlay these white lines on top of your original footage.
            
    - **Organic (Procedural Edge Wear and Dirt):** Edge detection filters are the key to creating procedural dirt maps.
        
        1. Take your render's Ambient Occlusion or Normal pass and feed it into a Filter node set to Kirsch to get a clean edge/cavity map.
            
        2. Separately, generate a Noise or Musgrave texture for your dirt pattern.
            
        3. Use a Mix node set to Multiply to combine the edge map with the noise texture.
            
        4. The result is a mask where the dirt texture appears only in the crevices and on the edges of your objects. You can use this final mask to mix in a rust or dirt color for highly realistic procedural texturing in the compositor.
            
    - **Organic (Animated "Pencil Sketch" Effect):** To create a look similar to the "Take on Me" music video:
        
        1. Use a Filter node set to Sobel on your footage to generate a constantly changing line drawing.
            
        2. On a separate branch, use a Posterize node on your footage to reduce its color palette to a few flat shades.
            
        3. Multiply the Sobel output over the Posterize output. This combines the hard black lines with the flat, cartoonish colors, creating a highly stylized rotoscoping effect.