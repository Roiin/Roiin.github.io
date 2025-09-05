- **Editor:** Compositor Node Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Generates a solid, uniform block of user-defined color. It acts as a simple, infinite source for any single color you need in your node tree.
    
- **Key Properties & Settings:**
    
    - **Color Picker (Property):** The main interface for selecting the desired color and its alpha (transparency) value.
        
    - **Color (Socket):** Outputs the chosen RGBA color value.
        
- **Practical Application:** While simple, this node is a fundamental building block for color manipulation and creating utility mattes.
    
    - **Molecular (Color Grading Foundation):** Use a Mix node set to Overlay or Soft Light with a low factor (e.g., 0.1-0.2). Feed your main render into one socket and a warm orange or cool blue from an RGB node into the other to apply a consistent, stylized color tint to the entire image, unifying the mood. This is a quick way to create a "sepia" or "moonlit" effect.
        
    - **Molecular (Solid Background Creation):** When compositing an object with an alpha channel (like a logo or a character render), use the RGB node as the background color input for an Alpha Over node. This is the simplest and most efficient way to place your rendered element on a solid-colored backdrop.
        
    - **Molecular (Stylized Vignettes):** The Vignette node darkens the edges of an image, typically to black. By feeding a dark desaturated blue or a deep red from an RGB node into the Vignette node's color socket, you can create a more artistic and less harsh vignette that complements the image's overall color palette.
        
    - **Organic (Color Replacement):** Use a Color Key node to isolate a specific color in your footage (e.g., a green prop on set). Use the resulting matte as the factor in a Color Mix node to replace that specific color with a new one supplied by the RGB node, allowing for powerful digital color changes in post-production without complex masking.