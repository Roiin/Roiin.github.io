- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** Reduces the number of distinct color tones in an image by quantizing or "stepping" the color values. This converts smooth gradients into flat, distinct bands of color, creating a "posterized" or "cel-shaded" look.
    
- -**Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Steps (Socket):** The most important control. This integer value sets the number of color divisions per channel (Red, Green, and Blue). A low value (e.g., 2 or 3) will result in a very abstract image with few colors, while a higher value (e.g., 8) will be more subtle.
        
- **Practical Application:** This node is primarily used for creating non-photorealistic styles and for generating high-contrast masks from smooth gradients.
    
    - **Molecular (Toon Shader / Cel-Shading Effect):** This is its most popular and powerful use. By setting the Steps to a low value like 2, 3, or 4, you can instantly transform a photorealistic render into an image with flat, cartoon-like shading. This is the foundational "atom" for creating an animated or comic book style.
        
    - **Molecular (Creating Hard-Edged Masks):** If you have a soft, grayscale gradient (like a Mist pass or a soft mask) and you need to convert it into a few distinct, hard-edged bands, the Posterize node is perfect. Applying it with 3 Steps will turn a smooth gradient into three clean, separate regions of black, gray, and white, which can be used for tiered effects.
        
    - **Organic (Stylized Rotoscoping):** To create a look similar to the film "A Scanner Darkly" or the "Take on Me" music video:
        
        1. Take your live-action footage and run it through a Posterize node to flatten the colors into cartoonish blocks.
            
        2. On a separate branch, use a Filter node (set to Sobel or Kirsch) on the original footage to generate a black-and-white edge-detect "line art" layer.
            
        3. Use a Mix node set to Multiply to combine the line art over the posterized colors. This "organism" creates a complete, animated rotoscoped effect directly in the compositor.
            
    - **Organic (Abstract Motion Graphics):** By feeding an animated procedural texture (like a Noise texture) into a Posterize node, you can create a constantly shifting and simplifying pattern of color blobs. This can be an excellent and computationally cheap source for abstract backgrounds or animated textures in motion graphics design.