- **Editor:** Compositor Node Editor  
- **Node Group:** Keying
    
- **Core Function:** Generates a matte by isolating a specific color (chroma) and making it transparent, ignoring its brightness (luma). It is designed specifically for greenscreen and bluescreen keying, where the goal is to remove a uniformly colored background.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The input footage containing the chroma screen (e.g., the greenscreen shot).
        
    - **Key Color (Property):** The most important setting. Use the color picker to select the specific shade of green or blue from your footage that you want to remove.
        
    - **Acceptance (Socket):** Controls the tolerance or "width" of the selected color. A higher value will select a wider range of similar colors (e.g., slightly different shades of green), but may start to key out desired foreground colors.
        
    - **Falloff (Socket):** Softens the edge of the matte, creating a smoother transition between the foreground and the keyed background.
        
    - **White/Black Clip (Sockets):** Thresholds for refining the matte. Clip Black is used to crush the gray areas of the matte to pure black (making more of the foreground solid). Clip White is used to crush the grays to pure white (making more of the background transparent).
        
- **Outputs:**
    
    - **Image (Socket):** The original image with the new alpha channel applied (premultiplied).
        
    - **Matte (Socket):** The raw black-and-white grayscale matte. In a professional workflow, this is the most important output, as it allows you to refine the matte before applying it.
        
- **Practical Application:** This node is the starting point for almost all greenscreen/bluescreen compositing.
    
    - **Molecular (Basic Greenscreen Key):** The fundamental "molecule" for VFX.
        
        1. Load your greenscreen footage with a Movie Clip node.
            
        2. Connect it to the Image input of the Chroma Key node.
            
        3. Use the Key Color picker to select a representative mid-tone green from the screen.
            
        4. Adjust the Acceptance until the background is mostly gone, then fine-tune the Clip Black and Clip White sliders to get a clean matte (solid white subject on a solid black background).
            
        5. Use the Matte output as the Factor in a Set Alpha node applied to your original footage, or more simply, use the Image output directly. You can then Alpha Over this result onto your new background.
            
    - **Organic (Core/Edge Matte Refinement):** A single key is rarely perfect. A professional workflow involves creating multiple keys and combining them.
        
        1. **Core Matte:** Create a Chroma Key designed to get a perfect, solid matte for the core of your subject, even if it means losing some edge detail. Use a Dilate/Erode node to shrink this matte slightly (Erode).
            
        2. **Edge Matte:** Create a second Chroma Key designed to capture all the fine edge detail (like hair), even if the core of the subject has some holes.
            
        3. **Combine:** Use a Mix node set to Add or a Lighten math node to combine the solid core matte with the detailed edge matte. This "organism" results in a final matte that is solid in the middle with soft, detailed edges, which is the goal of high-end keying.
            
    - **Organic (Garbage Matte):** Before keying, you often have lights, crew, or tracking markers in the shot that are not part of the green screen.
        
        1. Create a rough animated Mask around your subject to block out all the "garbage."
            
        2. Multiply this "garbage matte" with your footage before it goes into the Chroma Key node. This removes the unwanted elements, allowing the keyer to focus only on the clean green screen area, which produces a much better result.