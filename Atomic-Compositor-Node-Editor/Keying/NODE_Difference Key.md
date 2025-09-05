- **Editor:** Compositor Node Editor  
- **Node Group:** Keying
    
- **Core Function:** Generates a matte by comparing two images and isolating everything that is different between them. It is designed for situations where you have a "clean plate" (a shot of just the background) and an identical shot with a foreground element added.
    
- **Key Properties & Settings:**
    
    - **Image 1 (Socket):** The input image that contains the foreground element you want to isolate (e.g., the actor standing in front of the background).
        
    - **Image 2 (Socket):** The "clean plate" input. This must be a shot of the exact same background with the exact same lighting and camera position, but without the foreground element.
        
    - **Channel (Property):** Selects whether to base the difference on Luma (brightness), Chroma (color), or Color (both). Color is the most common and reliable.
        
    - **Tolerance (Socket):** A threshold that controls how similar pixels must be to be considered "the same" and thus made transparent. A small amount of tolerance is needed to account for minor noise or compression differences between the two plates.
        
- -**Outputs:**
    
    - **Image (Socket):** The foreground image with the background removed.
        
    - **Matte (Socket):** The raw black-and-white grayscale matte of the foreground element.
        
- **Practical Application:** This is the ultimate keyer for static shots where a green screen is not an option. Its success is entirely dependent on how well the "clean plate" matches the main shot.
    
    - **Molecular (Static Shot Keying):** This is its primary and intended use. Imagine a scene where a character appears to materialize in an empty room.
        
        1. First, film a few seconds of the empty room with a locked-off camera. This is your "clean plate" (Image 2).
            
        2. Without moving the camera or changing the lighting, have the actor walk into the shot. This is your "action plate" (Image 1).
            
        3. In the Difference Key node, the node will compare the two frames. Everywhere they are identical (the background), it will become transparent. Where they are different (the actor), it will become opaque.
            
        4. The result is a perfect matte of the actor, which can then be used for the materialization effect, without ever needing a green screen.
            
    - **Organic (Garbage Matte Generation):** It can be used to automatically generate a matte to clean up a shot. Imagine your actor is in front of a green screen, but a light stand is also visible off to the side.
        
        1. Take a frame where only the light stand is visible (or paint it out to create a truly "clean" frame).
            
        2. Use the Difference Key to compare the frame with the light stand to the frame without it.
            
        3. The node will generate a perfect matte of just the light stand, which can then be used to remove it from the entire shot.
            
    - **Critical Note on Limitations:** This technique is extremely sensitive to any changes between the two plates. A slight camera bump, a change in lighting (like a cloud passing over the sun in an outdoor shot), or even video compression can ruin the key. It is almost exclusively used for locked-off, controlled shots. The Mix node set to Difference can also be used to manually build a similar effect, often providing more control through the use of RGB Curves on the output.