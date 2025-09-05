- **Editor:** Compositor Node Editor  
- **Node Group:** Mask
    
- **Core Function:** Generates a simple, animatable rectangular (box) or square mask. It is a basic procedural tool for creating simple mattes without needing to use the Mask Editor.
    
- **Key Properties & Settings:**
    
    - **Width / Height (Sockets):** Controls the dimensions of the box as a fraction of the total image size. A Width of 0.5 and Height of 0.5 would create a box that is half the render's width and half its height.
        
    - **X / Y (Sockets):** Sets the position of the box's center. (0.5, 0.5) is the exact center of the screen.
        
    - **Rotation (Socket):** Rotates the box around its center point.
        
- **Mask Operation Inputs:**
    
    - **Mask Type (Property):** Defines how this generated box interacts with an optional mask fed into the Mask input socket (Add, Subtract, Multiply).
        
    - **Mask (Socket):** An optional input for another grayscale mask, allowing you to combine this box with other shapes.
        
- **Outputs:**
    
    - **Mask (Socket):** The final black-and-white rectangular mask.
        
- **Practical Application:** While simple, this node is a workhorse for creating quick mattes for localized effects, garbage mattes, and motion graphics.
    
    - **Molecular (Simple Garbage Matte):** If you have an unwanted object in the corner of a static shot (like a light stand), you can use a Box Mask to create a black rectangle that covers it. Use a Mix node set to Multiply (or a Math (Minimum)) to combine this with your main alpha matte, effectively removing the unwanted area.
        
    - **Molecular (Letterboxing / Cinematic Bars):** To create the black bars for a cinematic aspect ratio:
        
        1. Create a Box Mask. Set its Width to 1.0 and its Height to a value like 0.2. Position it at the top of the screen (e.g., Y=0.9).
            
        2. Create a second Box Mask identical to the first, but position it at the bottom (e.g., Y=0.1).
            
        3. Use a Math (Maximum) or Mix (Add) node to combine these two masks into one.
            
        4. This procedural matte can then be used to add black bars over your footage.
            
    - **Organic (Localized Color Correction):** To brighten a specific rectangular area of the image:
        
        1. Create a Box Mask and position it over the desired area.
            
        2. **Crucially**, feed this mask into a Blur node to give it soft, feathered edges.
            
        3. Duplicate your image stream and apply a Color Balance or Exposure adjustment to one version.
            
        4. Use a Mix node. Connect the original image to the top, the corrected version to the bottom, and your blurred box mask to the Factor. The color correction will now be applied only within the soft-edged box.
            
    - **Organic (Animated Wipes and Reveals):** By animating the X or Y position of a Box Mask, you can create a simple but effective wipe transition. Animate the Width and Height from 0 to 1 to make a title or image "reveal" itself from the center of the screen.