- **Editor:** Compositor Node Editor  
- **Node Group:** Color
    
- **Core Function:** Flips the values of an image's color and/or alpha channels. For colors, it produces a photographic negative. For alpha or masks, it swaps the transparent and opaque areas.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The color or mask input to be inverted.
        
    - **Factor (Socket):** Controls the strength of the inversion. At 0, there is no effect. At 1, the image is fully inverted. Values in between produce a muted or "grayed-out" version.
        
    - **Color (Property Checkbox):** When checked, it inverts the R, G, and B color channels (e.g., white becomes black, blue becomes yellow).
        
    - **Alpha (Property Checkbox):** When checked, it inverts the alpha channel (e.g., fully opaque becomes fully transparent).
        
- **Practical Application:** This node is a fundamental utility for mask manipulation and creating certain visual effects.
    
    - **Molecular (Flipping a Mask):** This is its most common and critical use. Imagine you have created a mask that perfectly isolates a character. You want to apply a blur effect to everything except the character.
        
        1. Take the original character mask (where the character is white and the background is black).
            
        2. Feed it into an Invert node (with only Color checked).
            
        3. The output is a new mask where the background is white and the character is black.
            
        4. Use this inverted mask as the Factor for your Blur node. The blur will now be applied only to the background.
            
    - **Molecular (Creating a Photographic Negative):** A direct artistic use. Simply running a color image through the Invert node will produce a classic "negative" effect, which can be used for stylization, sci-fi scanner effects, or transitions.
        
    - **Organic (Difference Keying):** A "difference key" is a way to create a matte by finding the difference between a clean background plate and the same plate with an actor in it.
        
        1. Place the "clean plate" in the top socket of a Mix node and the "actor plate" in the bottom. Set the mode to Difference.
            
        2. The output will be black everywhere the images are identical, and show the actor's shape in color.
            
        3. To turn this into a usable mask, you desaturate it and then often need to use an Invert node to get the actor as white on a black background, which is the standard format for a matte.
            
    - **Organic (Working with Inverted Data):** Sometimes, data from other software can be inverted. For example, some programs might export a "roughness" map where black means rough and white means smooth (the opposite of Blender's convention). Instead of re-baking the texture, you can simply load the image and run it through an Invert node to flip the values, making it instantly compatible with your Blender workflow.