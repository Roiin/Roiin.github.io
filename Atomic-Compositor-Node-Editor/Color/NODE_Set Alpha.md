- **Editor:** Compositor Node Editor  
- **Node Group:** Color
    
- **Core Function:** Adds or replaces the alpha (transparency) channel of an image. It takes a color image and a separate grayscale image (the mask) and combines them into a single image with a new, user-defined alpha channel.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The color information you want to use. This image's own alpha channel will be ignored or replaced.
        
    - **Alpha (Socket):`** The grayscale mask that will become the new alpha channel. White areas in this mask will be opaque, black areas will be transparent.
        
    - **Mode (Property):`** Determines how the new alpha is applied.
        
        - Apply Mask: Multiplies the input Image's RGB channels by the new Alpha. This correctly creates a **Premultiplied** alpha image, which is standard for Blender. This is the mode you should use most of the time.
            
        - Replace Alpha: Simply attaches the new Alpha channel to the input Image's RGB channels without modifying them. This creates a **Straight** alpha image.
            
- **Practical Application:** This node is essential whenever you need to define transparency for an image that doesn't have it, or when you need to create transparency from a source other than the image itself.
    
    - **Molecular (Adding Alpha to an Opaque Image):** This is its most fundamental use. You have a JPG of a logo on a white background and you want to put it over your footage.
        
        1. Use a Luma Key or Color Key node on the logo image to create a black-and-white mask of the logo.
            
        2. Use a Set Alpha node. Connect the original color logo JPG to the Image socket.
            
        3. Connect the black-and-white mask to the Alpha socket.
            
        4. The output is now the logo with a proper transparent background, ready to be used with an Alpha Over node.
            
    - **Molecular (Creating a Solid Color with Alpha):** To create a solid color that can be faded in.
        
        1. Use an RGB node to create your color (e.g., solid black). Connect this to the Image socket of the Set Alpha node.
            
        2. Use a Value node or Time Curve to provide a value between 0 and 1. Connect this to the Alpha socket.
            
        3. The output is a solid black image whose transparency can be animated. This is a common way to create a "fade to black" effect when used with Alpha Over.
            
    - **Organic (Depth-Based Masking / Z-Keying):** A powerful technique for creating atmospheric haze.
        
        1. Take the Depth pass from your Render Layers. The depth pass is a grayscale map of distances.
            
        2. Feed this Depth pass into a Color Ramp node to remap the distances to a desired falloff (e.g., making things beyond 50m start to fade).
            
        3. Use a Set Alpha node. Connect your main rendered Image to the Image socket.
            
        4. Connect the output of your Color Ramp (the remapped depth) to the Alpha socket.
            
        5. The result is your original render, but now with transparency that increases with distance from the camera. When you Alpha Over this onto a solid color or a sky, you get perfect, depth-based fog.