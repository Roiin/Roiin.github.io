### **Node: Pixelate**

- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** Deliberately reduces the resolution of an image by grouping pixels into larger, solid-colored blocks, creating a "pixelated" or "mosaic" effect.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Size (Socket):** A vector input that controls the width and height of the resulting "super-pixels." A size of (8, 8) will create 8x8 pixel blocks.
        
- **Practical Application:** This node is used almost exclusively for stylistic effects, mimicking the look of old video games, censored footage, or digital abstraction.
    
    - **Molecular (8-Bit / Retro Game Look):** This is its most common creative use. By applying the Pixelate node with a moderate size (e.g., 4x4 or 8x8), you can instantly give a high-resolution render the characteristic blocky appearance of a classic video game sprite.
        
    - **Molecular (Censorship Effect):** To create the classic "blurred out" effect used to obscure faces or sensitive information on TV:
        
        1. Create a Mask (e.g., an Ellipse Mask) that follows the area you want to censor.
            
        2. Duplicate your image stream. On one branch, apply a Pixelate node with a large size.
            
        3. Use a Mix node. Connect the original footage to the top socket, the pixelated version to the bottom socket, and your animated mask to the Factor. The result is a clean censorship effect that follows the subject.
            
    - **Organic (Abstract Backgrounds and Transitions):** The Pixelate node is great for creating simple, abstract background elements for motion graphics.
        
        1. Take a piece of footage or a complex procedural texture.
            
        2. Apply a Pixelate node with a very large size to reduce it to a few large, shifting blocks of color.
            
        3. You can then use this heavily abstracted version as a simple, non-distracting background for text or other graphic elements.
            
    - **Organic (Glitch / Digital Distortion Effect):** The Pixelate node can be a key component of a digital glitch "molecule."
        
        1. Use a Time node and some Math nodes (Modulo, Sine) to create a value that randomly jumps between a small number (e.g., 1) and a large number (e.g., 32).
            
        2. Feed this animated, glitchy value into the Size input of the Pixelate node.
            
        3. The result is an image that is normally sharp but will suddenly and erratically break down into large pixels, creating a convincing digital interference effect.