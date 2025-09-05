- **Editor:** Compositor Node Editor  
- **Node Group:** Keying
    
- **Core Function:** A comprehensive, "all-in-one" solution for greenscreen and bluescreen removal. It combines a sophisticated chroma keyer with integrated despill, edge detection, and matte refinement tools, streamlining the entire keying process into a single, powerful node.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input (your greenscreen footage).
        
    - **Key Color (Property):** The target background color to be removed. Use the color picker on your footage. Can also be fed a clean background plate from the Keying Screen node for more accuracy.
        
- **Primary Controls (The Workflow):**
    
    1. **Keying (Screen Balance):** The initial color selection. Adjust this to get the best possible initial separation between foreground and background.
        
    2. **Matte Finesse (Clip Black, Clip White):** The core refinement step. View the Matte output. Increase Clip Black to make the background fully black. Decrease Clip White to make the foreground fully white. Find the balance that creates a solid matte.
        
    3. **Edge Handling (Edge Kernel Radius/Tolerance):** This is for fine detail like hair. The node has a separate algorithm for edges that isn't affected by the Clip settings. View the Edge Kernel output to visualize what the node considers an "edge" and adjust these parameters to capture fine details without creating a halo.
        
    4. **Matte Post-Processing (Dilate/Erode, Feather):** Final cleanup. Use a small negative Dilate value to "choke" the matte and remove green edges. Use Feather to soften the matte for a better blend.
        
    5. **Despill (Despill Factor, Despill Balance):** The last step. Increase the Factor to neutralize the green light spilling onto your subject.
        
- **Mask Inputs:**
    
    - **Garbage Matte (Socket):** Connect a mask here to forcefully remove areas from the key (e.g., lights, crew, tracking markers).
        
    - **Core Matte (Socket):** Connect a mask here to forcefully keep areas in the key, useful for foreground objects that are the same color as the screen.
        
- **Outputs:**
    
    - **Image (Socket):** The final, keyed, and despilled image with transparency. A quick and easy output for simple shots.
        
    - **Matte (Socket):** The refined black-and-white matte. **This is the most important output for a professional workflow.**
        
- **Practical Application:** This node is designed to be a complete keying pipeline.
    
    - **Molecular (One-Node Key):** For simple, well-lit shots, this node can do everything.
        
        1. Connect your footage, pick the Key Color.
            
        2. View the Matte output and adjust Clip Black/White for a solid result.
            
        3. Adjust Despill until the green fringe is gone.
            
        4. Use the Image output and Alpha Over it onto your new background.
            
    - **Organic (Professional Keying Workflow):** Even with this powerful node, the best practice is to separate the keying and despilling operations.
        
        1. **Pull the Matte:** Use a Keying node and focus only on getting the absolute best Matte output possible. Tweak all the settings for a perfect black and white matte, and ignore the Image output and Despill section.
            
        2. **Despill the Color:** On a separate branch, take your original footage and run it through a Color Spill node (or a second Keying node used only for its despill function).
            
        3. **Combine:** Use a Set Alpha node. Connect the clean, despilled color image to the Image socket and the perfect Matte from the first Keying node to the Alpha socket. This "organism" provides the highest quality and most control, as you are not compromising your matte quality for your despill quality, or vice-versa.
            
    - **Organic (Using the Keying Screen):** For static or locked-off shots, you can generate an ideal background color plate using the Keying Screen node. Feeding this into the Key Color input of the Keying node gives the algorithm a perfect reference of the screen it needs to remove, resulting in a much cleaner initial key and requiring less tweaking of the Clip values.