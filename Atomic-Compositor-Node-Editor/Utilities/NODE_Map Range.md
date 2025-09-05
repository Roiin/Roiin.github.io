- **Editor:** Compositor Node Editor
- **Node Group:** Utilities
    
- **Core Function:** A powerful utility that remaps a numerical value from one range to another. It is the fundamental "translator" for controlling any node's parameters with the output of another node.
    
- **Key Properties & Settings:**
    
    - **Value (Socket):** The input number to be remapped.
        
    - **From Min / From Max (Sockets):** Defines the input range. For example, if you are using the output of a Noise Texture, you would set these to 0 and 1.
        
    - **To Min / To Max (Sockets):** Defines the output range. This is the new range you want your value to fit into.
        
    - **Clamp (Property Checkbox):** When checked, it ensures the output value never goes outside the To Min / To Max range, even if the input value exceeds the From range. This is crucial for preventing unexpected results.
        
    - **Interpolation Type (Property):** Allows for non-linear remapping, with Smooth Step providing a nice ease-in/ease-out effect.
        
- **Outputs:**
    
    - **Result (Socket):** The final, remapped numerical value.
        
- **Practical Application:** This node is the "gearbox" of a procedural setup. It connects the "engine" (like a texture or time node) to the "wheels" (like a blur size or color value) and controls the ratio.
    
    - **Molecular (Controlling Blur with Noise):** You want a blur effect that flickers randomly.
        
        1. Create a Noise Texture. Its output is a random value between 0 and 1.
            
        2. A blur size of 0 to 1 is very weak. You want a blur between 0 and 50 pixels.
            
        3. Use a Map Range node. Connect the Noise Texture to the Value.
            
        4. Set From Min=0, From Max=1.
            
        5. Set To Min=0, To Max=50.
            
        6. Connect the Result to the Size input of a Blur node. The blur will now flicker randomly between 0 and 50.
            
    - **Molecular (Animating with Time):** You want an object to rotate 360 degrees over 100 frames.
        
        1. Use a Scene Time node and take the Frame output.
            
        2. Use a Map Range node. From Min=1, From Max=100. To Min=0, To Max=360.
            
        3. Connect the Result to the Angle input of a Rotate node. The object will now perform a perfect 360-degree rotation over the first 100 frames.
            
    - **Organic (Depth-Driven Effects):** To make an object fade out with distance from the camera:
        
        1. Take the Depth pass from your Render Layers.
            
        2. Use a Map Range node. Let's say you want the fade to happen between 10 and 50 meters from the camera.
            
        3. Set From Min=10, From Max=50.
            
        4. You want to map this to an opacity value. Set To Min=1 (fully opaque) and To Max=0 (fully transparent). Enable Clamp.
            
        5. The Result is now a perfect procedural fade-out mask based on Z-depth. You can use this as the Factor in a Set Alpha or Mix node.