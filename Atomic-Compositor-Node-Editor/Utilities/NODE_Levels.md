- **Editor:** Compositor Node Editor  
- **Node Group:** Utilities
    
- **Core Function:** An analytical node that reads the color information of an entire input image and outputs statistical data about it, such as the average color (Mean) and the overall contrast (Standard Deviation).
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be analyzed.
        
    - **Channel (Property):** Selects which channel(s) to analyze. Luminance is often the most useful for brightness-based analysis.
        
- **Outputs:**
    
    - **Mean (Socket):** Outputs a single value (or color, if in Combined mode) representing the average value of all the pixels in the image. For Luminance, this is a direct measure of the image's overall brightness.
        
    - **Standard Deviation (Socket):** Outputs a single value representing the statistical standard deviation. This is a direct measure of the image's overall contrast. A low value means the image is flat and gray; a high value means it has deep blacks and bright whites.
        
- **Practical Application:** This is an advanced node for creating "intelligent" or "adaptive" node setups that can automatically adjust their behavior based on the content of the input image.
    
    - **Molecular (Auto-Exposure / Brightness):** This is its most powerful and common use case. You can build a "molecule" that automatically corrects the brightness of any input image to a consistent level.
        
        1. Feed your image into a Levels node (set to Luminance).
            
        2. You want your final image to have an average brightness of, for example, 0.5 (middle gray).
            
        3. Use a Math node set to Divide. In the top socket, put your target value (0.5). In the bottom socket, connect the Mean output from the Levels node.
            
        4. Take your original color image and use a Mix node set to Multiply. Connect the output of the Divide node as the second color input.
            
        5. This "organism" will analyze any input image, calculate how far its average brightness is from your target, and automatically multiply its brightness to compensate. A dark image will be brightened, and a bright image will be darkened, all procedurally.
            
    - **Organic (Adaptive Contrast):** In the same way, you can use the Standard Deviation output to build a system that automatically adjusts the contrast of an image to match a target contrast level. This is extremely useful for automatically matching footage from different cameras that might have been shot with different contrast settings.
        
    - **Organic (Content-Aware Effects):** You can use the outputs to drive creative effects. For example, you could connect the Mean output to the Size of a Glare node. The result would be an effect where darker images get a very subtle glow, while brighter images get a much stronger, more intense glow, all without any manual keyframing.