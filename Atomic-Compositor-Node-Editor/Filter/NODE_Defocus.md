- **Editor:** Compositor Node Editor
- **Node Group:** Filter  (Blur)

- **Core Function:** Simulates a realistic camera lens blur (depth of field) by using a Z-depth pass to intelligently vary the blur amount based on an object's distance from the camera. It is the primary tool for achieving photorealistic, data-driven DoF in post-production.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input from your Render Layers.
        
    - **Z (Socket):** The crucial Z-depth pass input, also from your Render Layers.
        
    - **Use Camera Settings (Property Checkbox):** When enabled, it automatically uses the focus distance and f-Stop set in the 3D scene's camera object, allowing for intuitive setup directly in the 3D viewport.
        
    - **f-Stop (Socket):** The main artistic control. Just like a real camera, a lower f-Stop value (e.g., 2.8) creates a much stronger, shallower depth of field effect, while a higher value (e.g., 22) keeps more of the image in focus.
        
    - **Focus Distance (Socket):** Manually sets the distance from the camera that will be perfectly in focus. Can be keyframed for a "rack focus" effect.
        
    - **Bokeh Type (Property):** Defines the shape of the out-of-focus highlights (e.g., Triangle, Hexagon, Octagon) to simulate the camera's iris blades.
        
    - **Max Blur (Socket):** A performance setting that caps the maximum blur radius, preventing extreme calculations on distant objects.
        
    - **No Z-buffer (Property Checkbox):** A special mode that tells the node to interpret the Z input not as distance data, but as a direct grayscale map for blur amount (black=sharp, white=blurry). This allows for mask-driven effects similar to the Bokeh Blur node.
        
- **Practical Application:** This is the go-to node for achieving cinematic, physically-based depth of field that integrates seamlessly with your 3D scene's camera.
    
    - **Molecular (Cinematic Depth of Field):** The primary use case.
        
        1. In your View Layer Properties, ensure the Z (Depth) pass is enabled.
            
        2. Connect the Image and Z outputs from your Render Layers node to the Defocus node.
            
        3. Check Use Camera Settings and adjust the Depth of Field -> Distance and Aperture -> F-Stop on your actual camera object in the 3D scene for an interactive, WYSIWYG setup.
            
    - **Molecular (Rack Focus):** To create a classic cinematic shot where focus shifts from a foreground to a background object:
        
        1. Uncheck Use Camera Settings.
            
        2. Animate the Focus Distance value in the Defocus node directly, setting keyframes for the start and end focus distances.
            
    - **Organic (The "Focus Pull" Trick):** A standard Defocus cannot make a blurry foreground object fully transparent to see what's behind it. To achieve a true "focus pull" effect:
        
        1. Render your scene in two passes: a Foreground layer and a Background layer.
            
        2. Use two Defocus nodes, one for each layer.
            
        3. Drive the Focus Distance or f-Stop of both nodes with the same animated value (e.g., from a Time or Value node), but use a Math node to invert the effect for one of them.
            
        4. As the background sharpens, the foreground blurs into transparency, and vice-versa. Alpha Over the results to combine them.
            
    - **Critical Note on Artifacts:** The Defocus node relies on the Z-pass, which is not anti-aliased. This can create harsh, aliased edges on out-of-focus objects. To mitigate this, you can slightly blur the Z-pass before it enters the node, or render at a higher resolution and scale down the final result. For maximum quality on tricky shots, the Bokeh Blur node driven by a manually cleaned-up Z-pass can sometimes yield better results.