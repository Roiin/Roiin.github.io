- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** Intelligently fills in transparent or masked areas of an image by extending and extrapolating the colors and textures from the surrounding pixels. It is a powerful "content-aware fill" tool for removing small unwanted objects or fixing holes in a matte.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The input image that contains transparent or masked "holes" that need to be filled.
        
    - **Distance (Socket):** Controls how many pixels the inpainting effect will extend inward from the edges of the hole. Small values (2-4) are best for clean results.
        
- **Practical Application:** This node is a problem-solver, used to digitally paint out small imperfections in a procedural and often automatic way.
    
    - **Molecular (Wire Removal):** This is its classic and intended use. To remove a thin wire or a tracking marker from a shot:
        
        1. Create a tight, precise Mask that covers only the wire.
            
        2. Use this mask with a Set Alpha or Keying node to "cut out" the wire from the image, leaving a transparent hole where it used to be.
            
        3. Feed this "holy" image into an Inpaint node.
            
        4. The Inpaint node will look at the pixels on either side of the transparent line (e.g., the blue sky) and fill in the gap, seamlessly removing the wire from the shot.
            
    - **Molecular (Fixing Chroma Key Holes):** When you key out a green screen, sometimes small parts of the subject that are the same color as the screen (like a green reflection on a shiny object) will also get keyed out, leaving a small hole. The Inpaint node can fix this.
        
        1. After keying, your subject has a transparent hole in it.
            
        2. Run the keyed subject through an Inpaint node with a small Distance. It will fill the hole with the surrounding colors of the subject's texture, patching it up before you composite it over the new background.
            
    - **Organic (Edge Extension for Compositing):** A critical step in professional green screen compositing to prevent background colors from "bleeding" through the semi-transparent edges of a key.
        
        1. Take your final keyed character (the RGBA image).
            
        2. Feed it into an Inpaint node with a Distance of 4-8 pixels. This will "bleed" the character's own edge colors outwards into the transparent areas.
            
        3. Now, when you Alpha Over this inpainted version onto your new background, any semi-transparent pixels at the edge of the matte (e.g., around hair) will be blending with the character's own extended colors instead of the original green screen color, resulting in a perfectly clean and seamless edge. This is a crucial "molecule" for high-quality keying.