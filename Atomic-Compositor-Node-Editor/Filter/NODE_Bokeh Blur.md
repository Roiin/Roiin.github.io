- **Editor:** Compositor Node Editor  
- **Node Group:** Filter (Blur)
    
- **Core Function:** Applies a high-quality, camera-style blur to an image, where both the blur amount and the shape of the out-of-focus highlights (the "bokeh") are manually controllable. Unlike the Defocus node, it is driven by a mask input rather than camera data.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input to be blurred.
        
    - **Bokeh (Socket):** A special input designed to be connected to a Bokeh Image node. This allows you to define a custom shape (e.g., hexagonal, rounded, anamorphic) for the highlights, which is a key part of creating a specific photographic look.
        
    - **Size (Socket):** The crucial control input. This is a grayscale mask that defines the blur amount for every pixel. Black areas in the mask will be perfectly sharp (blur size 0), while white areas will receive the maximum blur amount.
        
    - **Max Blur (Property):** A slider that sets the maximum blur radius in pixels that corresponds to the white areas of the Size input mask.
        
    - **Bounding Box (Socket):** A utility input that allows you to connect a Box Mask or Mask node to limit the blur calculation to a specific region of the image. This is a performance optimization, useful for previews and look development.
        
- **Practical Application:** This node is for "art-directed" depth of field, giving you pixel-perfect control over what is sharp and what is blurry, independent of 3D data.
    
    - **Molecular (Art-Directed Focus):** This is its primary use. If you want to draw the viewer's eye to a specific object or character, you can create a custom mask for it.
        
        1. Create a soft, feathered mask (using Ellipse Mask or Mask node) around your subject.
            
        2. Invert this mask, so the subject is black and the background is white.
            
        3. Feed this inverted mask into the Size socket of the Bokeh Blur node.
            
        4. The result is a beautiful blur that wraps around your subject, keeping them perfectly in focus while softening the background. This is often faster and more creatively flexible than using a full Defocus.
            
    - **Organic (Z-Depth Driven Blur):** You can replicate the behavior of the Defocus node with more control.
        
        1. Take the Z (depth) pass from your Render Layers.
            
        2. Feed it into a Color Ramp node. This is your "focus tool." By adjusting the color ramp, you can precisely define a narrow band of gray/white that represents your desired focal plane.
            
        3. Connect the output of the Color Ramp to the Size input of the Bokeh Blur node. You now have a depth-of-field effect where the focus point and depth of the focus plane are controlled with the Color Ramp.
            
    - **Organic (Custom Anamorphic Bokeh):** To achieve a specific cinematic lens style:
        
        1. Create a Bokeh Image node (e.g., 8 flaps, 0.8 roundness).
            
        2. Pipe its output into a Transform node and scale the Y-axis to 0.5 to create an oval.
            
        3. Connect this transformed shape into the Bokeh input of the Bokeh Blur node.
            
        4. Drive the Size input with a Z-depth pass or a custom mask.
            
        5. The result is a depth-of-field effect that has the characteristic vertically-squashed highlights of an anamorphic lens, a highly sought-after cinematic "molecule."