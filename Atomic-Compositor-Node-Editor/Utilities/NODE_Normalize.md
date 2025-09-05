- **Editor:** Compositor Node Editor  
- **Node Group:** Utilities
    
- **Core Function:** Analyzes an entire input image (or data pass), finds its absolute darkest and brightest values, and then stretches or compresses that range to fit perfectly between 0.0 (black) and 1.0 (white).
    
- **Key Properties & Settings:**
    
    - **Value (Socket):** The grayscale input to be normalized.
        
- **Outputs:**
    
    - **Value (Socket):** The remapped, full-contrast grayscale output.
        
- **Practical Application:** This node is an "auto-contrast" tool. It's primarily used to make non-visual data, which might exist in a very small or very large numerical range, visible and usable for compositing.
    
    - **Molecular (Visualizing the Z-Depth Pass):** This is its most common and essential use. A raw Z-depth pass from a Render Layers node often looks like a completely white or black image. This is because the actual distance values might range from, for example, 10.0 to 1000.0 units. These numbers are far outside the visible 0-1 range.
        
        1. Connect the Depth output from your Render Layers node to the Value input of a Normalize node.
            
        2. Connect the output to a Viewer node.
            
        3. The Normalize node will find the closest point (e.g., 10.0) and map it to black (0.0), find the farthest visible point and map it to white (1.0), and stretch all the values in between. The result is a perfectly clear, full-contrast grayscale image of your scene's depth, ready to be inspected or used as a mask.
            
    - **Molecular (Maximizing Contrast on Any Mask):** If you have a procedural mask that is very low contrast (e.g., all the values are between 0.4 and 0.6), a Normalize node will instantly stretch those values to a full 0-1 range, giving you a punchy, high-contrast version of the mask. This is a quick alternative to manually adjusting a Color Ramp or Levels node.
        
    - **Organic (Creating an Automatic Height Map):**
        
        1. Take the Position pass from your Render Layers.
            
        2. Use a Separate XYZ node and take the Z output. This gives you a grayscale map of the world height of every point in your scene. Like the Z-depth, this will likely be outside the visible range.
            
        3. Feed this Z position data into a Normalize node.
            
        4. The output is now a perfect, normalized height map. You can use this with a Color Ramp to, for example, procedurally add snow (white) only to the highest peaks (the brightest parts of the normalized map) of your mountains.