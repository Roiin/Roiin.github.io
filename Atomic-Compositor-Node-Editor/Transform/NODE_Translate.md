- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- -**Core Function:** Moves (translates) an image horizontally and vertically. It is a dedicated tool for repositioning elements without altering their scale or rotation.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **X / Y (Sockets):** Controls the movement in pixels along the horizontal and vertical axes. These values are animatable.
        
    - **Relative (Property Checkbox):** When checked, the X and Y values are treated as a percentage of the image dimensions rather than absolute pixels, which can be useful for resolution-independent setups.
        
    - **Wrapping (Property):** Determines what happens when the image is moved past the frame boundary. None is the default. Wrap X, Y, or Both will cause the pixels that move off one edge to reappear on the opposite edge, creating a seamless tiling effect.
        
- **Practical Application:** While the Transform node can also translate, this dedicated node is useful for clarity, simplicity, and its unique Wrapping feature.
    
    - **Molecular (Simple Repositioning):** Its most basic use is to adjust the composition of a shot. If an element is slightly off-center, you can use the Translate node to nudge it into the perfect position.
        
    - **Molecular (Animating a Pan/Scroll):** By animating the X or Y value, you can make an image slide across the screen. This is a common way to pan across a large still image or to create scrolling text.
        
    - **Organic (Seamlessly Tiling Backgrounds):** The Wrapping feature is key for this.
        
        1. Take a texture that is designed to be tileable (like a procedural Noise Texture or a seamless photo texture).
            
        2. Connect it to a Translate node and enable Wrapping for both axes.
            
        3. Now, when you animate the X or Y values, the texture will scroll infinitely without any visible seams. This is perfect for creating endlessly moving backgrounds for 2D animation or motion graphics.
            
    - **Organic (Procedural Camera Shake):** For a simple, convincing 2D camera shake:
        
        1. Add a Translate node to your final footage.
            
        2. In the Graph Editor, select the X Location property and add a Noise F-Curve Modifier. Adjust its Scale and Strength for the desired shake frequency and intensity.
            
        3. Do the same for the Y Location property, but change the Phase or Offset of the noise so the X and Y shakes are not identical.
            
        4. This "molecule" creates a procedural, non-repeating camera shake. You'll likely need to add a Scale node afterward to zoom in slightly and hide the moving black borders.