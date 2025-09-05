- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Mix)
    
- **Core Function:** Merges two images by comparing their Z-depth values on a pixel-by-pixel basis. It intelligently chooses which image is "in front" and should be visible, allowing for the correct integration of elements from different render layers or scenes.
    
- **Key Properties & Settings:**
    
    - **Image (Top Sockets):** The first image and its corresponding Z (depth) pass.
        
    - **Image (Bottom Sockets):** The second image and its corresponding Z (depth) pass.
        
    - **Use Alpha (Property Checkbox):** When checked, it respects the alpha channel of the "winning" pixel. If the pixel that is closer to the camera is also transparent, the image behind it will show through. This is essential for compositing transparent elements like glass or smoke.
        
    - **Anti-Alias Z (Property Checkbox):** Applies a small amount of filtering to the Z-buffer comparison. This is crucial for avoiding jagged, aliased edges ("jaggies") where the two elements intersect. It should almost always be enabled.
        
- **Outputs:**
    
    - **Image (Socket):** The final composited image, with elements correctly sorted by depth.
        
    - **Z (Socket):** The combined Z-depth map of the resulting image. This allows you to chain multiple Z Combine nodes together to composite a third element, then a fourth, and so on.
        
- **Practical Application:** This node is the solution for complex holdouts and intersections that are impossible to achieve with a simple Alpha Over.
    
    - **Molecular (Correct Scene Integration):** This is its primary purpose. Imagine you have two separate render layers: one with a character (Scene A) and one with a column (Scene B). If the character is meant to walk behind the column, a simple Alpha Over will always place the character on top.
        
        1. In a Z Combine node, connect Scene B's Image and Z-depth to the top inputs.
            
        2. Connect Scene A's Image and Z-depth to the bottom inputs.
            
        3. The node will compare the depth of the character and the column for every pixel. Where the column is closer to the camera, it will show the column's pixels. Where the character is closer, it will show the character's pixels. This creates a perfect composite where the character is correctly occluded by the column.
            
    - **Organic (Integrating Volumetrics):** For placing an object inside a volume like smoke or fog that was rendered in a separate pass.
        
        1. Z-Combine your main object (e.g., a spaceship) with the volumetric smoke pass.
            
        2. The node will correctly interleave the spaceship and the smoke, making it appear as if the ship is truly flying through the volumetric cloud, with wisps of smoke correctly appearing both in front of and behind the ship. This is impossible with Alpha Over.
            
    - **Organic (Inserting 2D Elements into 3D Space):** To place a 2D image plane (like a video screen or a matte painting) into a 3D scene at a specific depth.
        
        1. Connect your 3D render and its Z-pass to the top inputs.
            
        2. Connect your 2D image to the bottom Image input.
            
        3. For the bottom Z input, you need to create a flat plane of depth. This can be done by using an RGB node (set to a gray value) or a Value node connected to a Set Alpha node. The single value (e.g., 15.0 for 15 units from the camera) will be used as the depth for the entire 2D image.
            
        4. The Z Combine node will then correctly composite the scene, occluding the 2D plane with any 3D objects that are closer than 15 units, and showing the plane in front of any objects that are farther than 15 units.