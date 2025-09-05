- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** Mirrors an image along its horizontal and/or vertical axes.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be flipped.
        
    - **Flip X (Property Checkbox):** When checked, flips the image horizontally (left becomes right and vice versa).
        
    - **Flip Y (Property Checkbox):** When checked, flips the image vertically (top becomes bottom and vice versa).
        
- **Practical Application:** A straightforward utility for correcting orientation and creating symmetrical patterns and effects.
    
    - **Molecular (Correcting Footage):** Its most direct use is to fix footage that was recorded upside down or mirrored. Check the appropriate axis to reorient the image correctly.
        
    - **Molecular (Creating Reflections):** A simple way to create a reflection for an object on a flat plane (like a floor).
        
        1. Take your rendered object (with an alpha channel).
            
        2. Feed it into a Flip node with Flip Y checked.
            
        3. Use a Translate node to move this flipped version down so it sits below the original object.
            
        4. You can then lower its opacity, add some blur, or use a Mix node to tint it to create a more realistic reflection, which you would then composite behind the original object.
            
    - **Organic (Symmetrical "Rorschach" Patterns):** You can create complex, symmetrical, inkblot-style patterns.
        
        1. Take an asymmetrical texture, like a Noise or Magic texture.
            
        2. Crop or Box Mask one half of the texture.
            
        3. Feed this half-texture into a Flip node with Flip X checked.
            
        4. Use a Translate node to position this flipped half next to the original half.
            
        5. Add or Alpha Over the two halves together. The result is a perfectly symmetrical, often organic-looking pattern that can be used for backgrounds, sci-fi displays, or creature designs.
            
    - **Organic (Flipping Data Maps):** This node also works on non-color data. If you have a gradient or a mask that needs to be reversed, the Flip node is the simplest way to do it. For example, a Linear Gradient texture normally runs from left to right. Running it through a Flip X will make it run from right to left.