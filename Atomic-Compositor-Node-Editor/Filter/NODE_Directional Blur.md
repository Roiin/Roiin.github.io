- **Editor:** Compositor Node Editor  
- **Node Group:** Filter (Blur)
    
- **Core Function:** Applies a blur along a specific angle or path, creating a streaking effect. It's primarily used to simulate fast linear motion, rotational motion (spin), or zooming, offering an artistic alternative to the data-driven Vector Blur.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Iterations (Property):** The quality of the blur. Higher values create a smoother streak but take longer to compute.
        
    - **Wrap (Property Checkbox):** When the blur extends past the image boundary, this option makes it wrap around to the other side. Useful for creating seamlessly tiling blurred textures.
        
- **Mode-Specific Settings:**
    
    - **Type (Property):** Selects the blur mode: Streaks, Spin, or Zoom.
        
    - **Streaks Mode:**
        
        - **Distance (Socket):** Controls the length of the blur streaks in pixels.
            
        - **Angle (Socket):** Sets the direction of the streaks in degrees.
            
    - **Spin Mode:**
        
        - **Angle (Socket):** The main control, setting how many degrees the image is "spun" to create the blur.
            
        - **Center X/Y (Sockets):** Sets the pivot point for the rotation.
            
    - **Zoom Mode:**
        
        - **Distance (Socket):** A scaling factor that controls how much the image is "zoomed" to create the blur. Positive values zoom in, negative values zoom out.
            
        - **Center X/Y (Sockets):** Sets the center point for the zoom effect.
            
- **Practical Application:** This is the go-to tool for adding stylized motion effects when you don't have or don't want to use a Vector pass.
    
    - **Molecular (Linear Motion Blur):** To fake the look of a fast-moving object or a quick camera pan.
        
        1. Set the Type to Streaks.
            
        2. Adjust the Distance to control the speed and the Angle to match the direction of motion.
            
        3. This is excellent for adding motion blur to 2D graphic elements or footage that lacks blur. To apply it to a single object, you would first need to isolate that object with a mask.
            
    - **Molecular (Spinning Wheels):** To make the wheels of a stationary car look like they are spinning rapidly.
        
        1. Create a circular mask that isolates just the car's wheel.
            
        2. Set the Type to Spin and center it on the wheel's axle.
            
        3. Increase the Angle to a high value (e.g., 30-60 degrees) to create a strong rotational blur.
            
        4. Composite this blurred wheel back over the original image.
            
    - **Organic (Crash Zoom / Vertigo Effect):** To simulate a rapid camera zoom.
        
        1. Set the Type to Zoom.
            
        2. Animate the Distance value, keyframing it from 0 to a high value over a few frames.
            
        3. This creates a blur that radiates from the center of the screen, perfectly faking the motion blur of a very fast zoom lens. This is a common effect in action sequences.
            
    - **Organic (Anamorphic Lens Flare):** While not its primary purpose, the Streaks mode is a key component in creating a classic horizontal anamorphic lens flare "molecule."
        
        1. Isolate the brightest highlights of your image.
            
        2. Use a Directional Blur in Streaks mode with the Angle set to 0 (horizontal) and a very large Distance.
            
        3. Color this long streak blue using a Mix node.
            
        4. Add this blue streak back over your main image to create the iconic sci-fi lens flare.