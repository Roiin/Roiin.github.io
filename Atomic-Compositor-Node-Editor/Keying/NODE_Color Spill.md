- **Editor:** Compositor Node Editor  
- **Node Group:** Keying
    
- **Core Function:** A specialized color correction tool designed to remove "color spill"—the unwanted colored light (usually green or blue) that reflects from a chroma key screen onto the foreground subject. It neutralizes this color contamination, restoring the subject's natural colors.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The input image that has the color spill (typically, this is the original footage before the key is applied).
        
    - **Channel (Property):** Selects the color to be suppressed. Green is used for greenscreens, Blue for bluescreens.
        
    - **Limit Channel (Property):** Selects the reference channel(s) for the suppression. A common setup for greenscreen is to limit by the Red and Blue channels.
        
    - **Algorithm (Property):** The method used for suppression. Simple is often effective and intuitive. Average provides a different calculation that can work better on certain footage.
        
    - **Fac (Socket):** A blend factor that controls the overall strength of the despill effect.
        
- **Practical Application:** This node is not a keyer itself, but a crucial companion to a keyer. It is a mandatory step in any professional greenscreen composite to make the foreground element look believable.
    
    - **Molecular (Basic Spill Suppression):** The most direct and essential use case.
        
        1. Take your original greenscreen footage.
            
        2. Feed it into a Color Spill node.
            
        3. Set the Channel to Green. Often, the default settings are a good starting point.
            
        4. The output is your footage with the green reflections on the subject (e.g., on their hair, shoulders, and any reflective surfaces) neutralized and turned to a more natural gray or skin tone.
            
    - **Organic (The Professional Keying Workflow):** The Color Spill node is part of a larger "organism" for high-quality keying. The workflow is often non-intuitive but produces the best results.
        
        1. **Pull the Key:** Use a Keying or Chroma Key node on your original footage to generate the best possible Matte.
            
        2. **Suppress the Spill:** On a separate branch, take your original footage and run it through the Color Spill node to get a clean, despilled color version of your subject.
            
        3. **Re-apply the Matte:** Use a Set Alpha node (or an Alpha Convert and Multiply chain). Connect the clean, despilled color image to the Image input, and connect the high-quality Matte you generated in step 1 to the Alpha input.
            
        4. This "organism" ensures you get the best of both worlds: the sharpest possible matte from the original footage, and the cleanest possible color from the despilled footage. This is a far superior method to simply taking the Image output from a keying node.
            
    - **Organic (Edge Spill vs. Core Spill):** For very difficult shots, you can apply different amounts of spill suppression to the core of the subject and to their delicate edges.
        
        1. Create a "core" matte by eroding your main matte inward.
            
        2. Create an "edge" matte by subtracting the core matte from the main matte.
            
        3. Use these two mattes to mix between a heavily despilled version (for the core) and a more subtly despilled version (to preserve color detail in the hair and semi-transparent edges). This advanced technique provides the ultimate level of control.