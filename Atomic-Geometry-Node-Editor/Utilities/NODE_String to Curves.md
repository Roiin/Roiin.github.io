- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Converts an input string into a set of curve instances, with one instance for each character. It uses a specified font to generate the geometry and provides detailed controls for layout, spacing, and alignment.
    
- **Key Properties & Settings:**
    
    - **String (Socket - Input):** The text to be converted.
        
    - **Font (Property):** A data-block selector to choose the typeface to use.
        
    - **Size (Socket - Input):** Controls the overall scale of the generated text.
        
    - **Spacing (Character, Word, Line):** Floats to control the spacing between characters, words, and lines.
        
    - **Alignment (X and Y):** Dropdown menus to control the horizontal (Left, Center, Right) and vertical (Top, Middle, Bottom) alignment of the text block.
        
    - **Pivot Point (Property):** Determines the location of each character instance's origin (e.g., Midpoint, Bottom Left). This is crucial for applying transformations.
        
    - **Curve Instances (Socket - Output):** The primary output; a set of curve instances representing the text.
        
    - **Line (Socket - Output):** An integer attribute on the instances, identifying which line each character belongs to.
        
    - **Pivot Point (Socket - Output):** The calculated pivot point position for each instance, useful for custom transformations.
        
- **Practical Application:** This node is the foundation for any procedural text effect, such as creating a "wavy" title for an animated creature feature.
    
    1. **The Goal:** To make the letters of a title (e.g., "THE KRAKEN") move up and down in a sine wave.
        
    2. Use the String to Curves node to generate the text.
        
    3. **The Problem:** The output is a set of instances. A Set Position node won't work directly, as it affects the points inside the instances, not the instances themselves. You need to move the entire character instances.
        
    4. **The Solution:** Use a Translate Instances node.
        
        - To create the wave, you need to offset each character's position based on its location along the line of text. The Pivot Point output gives you this position.
            
        - Take the X component of the Pivot Point and feed it into a Math node set to 'Sine'. This will create a smooth, wavy value.
            
        - To make the wave animate, add the Scene Time (Seconds) to the X component before the sine function.
            
        - Use a Combine XYZ node to create a translation vector where the Y component is driven by your animated sine wave.
            
    5. Connect this vector to the Translation input of the Translate Instances node.
        
    6. **The Result:** The letters of your title will now bob up and down in a continuous, smooth wave, creating a dynamic and professional-looking motion graphic.