- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Mix)
    
- **Core Function:** Layers a foreground image with transparency on top of a background image. It is the fundamental and mathematically correct way to perform standard compositing operations, like placing a character over a background.
    
- **Key Properties & Settings:**
    
    - **Image (Top Socket):** The background image. The "bottom layer."
        
    - **Image (Bottom Socket):** The foreground image. The "top layer" that should have an alpha channel.
        
    - **Factor (Socket):** A global opacity multiplier for the foreground image. At 0, only the background is visible. At 1, the foreground is composited at its full opacity. This is useful for fading elements in or out.
        
    - **Convert Premultiplied (Property Checkbox):** A technical setting for managing alpha types. Blender's compositor works internally with "premultiplied" alpha. This box should be checked only if you are inputting an image that is known to use "straight" alpha, which is rare. Leaving this unchecked is correct 99% of the time.
        
- **Practical Application:** This is the primary "assembly" node. If the Mix node is the glue, Alpha Over is the precision tool for stacking transparent layers.
    
    - **Molecular (CG on Background Plate):** This is its most essential and common use.
        
        1. Connect your background footage (from an Image or Movie Clip node) to the top Image socket.
            
        2. Connect your CG render (from a Render Layers node, which has an alpha channel) to the bottom Image socket.
            
        3. The output will be your CG character or object perfectly placed on top of the live-action background.
            
    - **Molecular (Layering Graphics and Titles):** To place a lower-third title or a logo over your footage:
        
        1. Connect your main video to the top Image socket.
            
        2. Connect your title graphic (which must have an alpha channel) to the bottom Image socket.
            
        3. The result is a clean composite of the graphics over the video. You can animate the Factor from 0 to 1 to make the title fade in.
            
    - **Organic (Multi-Layer Scene Assembly):** In a complex VFX shot, you often render elements separately for more control (foreground, midground, background). Alpha Over is used to stack them back together correctly.
        
        1. Alpha Over Node 1: Place the Midground render over the Background render.
            
        2. Alpha Over Node 2: Take the output of the first node (which is now Midground + Background) and use it as the background input. Connect your Foreground render as the new foreground.
            
        3. By chaining Alpha Over nodes like this, you can correctly assemble a scene with many layers of depth, ensuring that each layer's transparency is handled properly. This is far more reliable than using Mix nodes for this task.
            
    - **Organic (Adding Atmospherics like Fog):** To add a layer of fog between your character and the background:
        
        1. First, composite your character over the background using Alpha Over.
            
        2. Separately, create your fog element (e.g., using a Texture node with some blur).
            
        3. Use a second Alpha Over node. Connect your Character+Background composite to the top socket, and your fog element to the bottom socket.
            
        4. This correctly layers the fog on top of everything. For a more realistic effect where the fog is behind the character, you would need to change the order of operations, compositing the fog over the background before compositing the character on top of that result.