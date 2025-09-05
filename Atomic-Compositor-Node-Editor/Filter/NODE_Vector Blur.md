- **Editor:** Compositor Node Editor  
- **Node Group:** Filter (Blur)
    
- **Core Function:** Creates accurate, per-pixel motion blur by using a Vector render pass. This pass stores the direction and speed of each pixel's movement between frames, allowing the node to streak the image in a physically plausible way.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input (the "beauty pass") from your Render Layers.
        
    - **Z (Socket):** The Z-depth pass from Render Layers. This helps the node handle overlapping objects correctly, preventing background pixels from incorrectly blurring over the foreground.
        
    - **Speed (Socket):** The crucial Vector pass from Render Layers. This is the data that drives the entire effect.
        
    - **Samples (Property):** Controls the quality of the blur. Low values can look "stepped" or dithered. Higher values (e.g., 32, 64) produce a much smoother, higher-quality result at the cost of processing time.
        
    - **Blur (Shutter) (Property):** Corresponds to a camera's shutter speed. A value of 0.5 is standard (a 180-degree shutter). A value of 1.0 creates a longer, more pronounced blur, while a value of 0.2 creates a short, crisp blur.
        
    - **Max Speed / Min Speed (Properties):** Clamping values that can help eliminate artifacts caused by extremely fast-moving pixels (e.g., from glitches or intersecting geometry).
        
- **Practical Application:** This is the professional, data-driven method for adding motion blur in post-production, which is almost always faster and more flexible than rendering motion blur directly from the 3D scene.
    
    - **Molecular (Standard Motion Blur):** This is the node's primary and intended use.
        
        1. In your View Layer Properties, ensure the Z (Depth) and Vector passes are enabled.
            
        2. Connect the Image, Z, and Vector outputs from your Render Layers node to the corresponding inputs on the Vector Blur node.
            
        3. Adjust the Blur (Shutter) value to control the overall strength of the effect.
            
        4. This will add realistic motion blur to anything moving in your scene—animated characters, vehicles, and even the background if the camera itself is moving.
            
    - **Organic (Isolating Blur for Problem Objects):** Hair, transparency, and volumes can sometimes cause artifacts with vector blur. The professional "molecule" to solve this is to use render layers.
        
        1. Place your problematic object (e.g., a character with hair) in its own View Layer. Render the background separately.
            
        2. Apply Vector Blur only to the character layer.
            
        3. Apply a separate Vector Blur to the background layer (this will handle the camera's motion).
            
        4. Use an Alpha Over node to composite the blurred character on top of the blurred background. This isolates the calculation and prevents the character's motion vectors from incorrectly affecting the background pixels.
            
    - **Organic (Art-Directed Motion):** While the blur is data-driven, you can still manipulate it.
        
        1. Take the Vector pass output and feed it into a Vector Math node set to Multiply.
            
        2. By multiplying the vector pass by a value greater than 1, you can exaggerate the motion blur for a stylized, high-speed effect.
            
        3. By multiplying it with a procedural texture, you could even make the motion blur appear "glitchy" or inconsistent, all while being based on the real motion from the scene.