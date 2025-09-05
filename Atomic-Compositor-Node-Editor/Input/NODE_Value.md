- **Editor:** Compositor Node Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Acts as a central, animatable controller for any numerical parameter, allowing a single value to drive multiple nodes simultaneously. It is the "master knob" for building complex and easily adjustable effects.
    
- **Key Properties & Settings:**
    
    - **Numeric Value (Property):** A single floating-point number field where you can input or keyframe a value.
        
    - **Value (Socket):** Outputs the number set in the properties.
        
- **Practical Application:** Its power comes not from what it does on its own, but how it connects and organizes other nodes.
    
    - **Molecular (Uniform Blur Control):** The Blur node has separate X and Y values. To create a uniform, non-streaked blur, you must keep these values identical. By feeding a single Value node into both the X and Y sockets of the Blur node, you can adjust the overall blur amount with one slider, ensuring it remains perfectly consistent.
        
    - **Molecular (Master Effect Controller):** Imagine you have a complex color grade, a vignette, and a film grain effect, each mixed over your base render using Mix nodes. You can plug a single Value node into the Factor socket of all three of these Mix nodes. This creates a "Master Intensity" slider. Keyframing this one value from 0 to 1 allows you to fade your entire post-processing look in or out smoothly and consistently across all effects.
        
    - **Organic (Linked Depth of Field and Vignette):** This is where it gets powerful. You want to create an effect where the image gets blurrier, and as it does, a vignette appears to focus the viewer's eye.
        
        1. Create a Value node named "Focus Intensity".
            
        2. Connect "Focus Intensity" to a Math (Map Range) node to control the f-Stop on a Defocus node (e.g., mapping 0-1 from the Value node to 16-1.4 on the f-Stop).
            
        3. Connect the same "Focus Intensity" value to the Size input of a Vignette node.
            
        4. Now, animating the single "Focus Intensity" value will simultaneously rack focus and strengthen the vignette, creating a sophisticated, linked visual effect that is controlled by a single, simple parameter. This is a basic "organism."