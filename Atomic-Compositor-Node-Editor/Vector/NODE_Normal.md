- **Editor:** Compositor Node Editor
- **Node Group:** Vector
    
- **Core Function:** Provides a fixed vector direction and calculates its relationship (dot product) to an incoming vector pass, primarily for relighting purposes.
    
- **Key Properties & Settings:**
    
    - **Normal (Socket - Input):** The source vector data, which should be connected to a World Space Normal pass from your render.
        
    - **Normal Direction (Property):** An interactive sphere used to manually set the direction of the virtual "light" you are adding in the composite.
        
    - **Normal (Socket - Output):** Outputs the fixed vector direction set by the Normal Direction property.
        
    - **Dot (Socket - Output):** The primary output for relighting, this is a grayscale image representing the dot product. Areas on the surface that face the Normal Direction are white (value of 1), while areas perpendicular are gray (0) and areas facing away are black (-1).
        
- **Practical Application:** This node is a cornerstone of professional compositing workflows for non-destructively adding a "rim light" or "kicker light" to a CG render after it has been completed, without needing to re-render the 3D scene.
    
    1. Begin with a **Render Layers** node (or an **Image** node loading a multi-layer EXR). Ensure you have rendered your scene with a "Normal" pass enabled.
        
    2. Connect the Normal socket from your render pass into the Normal (Socket - Input) of the **Normal Node**.
        
    3. In the **Normal Node**'s properties, click and drag on the Normal Direction sphere to point it from a direction you want your new light to come from (e.g., from the top-left and slightly behind the subject).
        
    4. The Dot (Socket - Output) now shows a grayscale image of your scene "lit" from this new direction. To gain more control, connect this Dot output into a **Color Ramp** node. By sliding the black and white stops on the ramp, you can control the hardness and falloff of your new light mask.
        
    5. Add a **Color Balance** node to your main beauty pass (Image output). Connect the output of the **Color Ramp** into the Fac (Factor) input of this **Color Balance** node.
        
    6. Now, adjust the Gain or Gamma controls on the **Color Balance** node. You will see the image get brighter, but only in the areas defined by your light mask. You can make the light warmer by tinting the gain towards yellow or orange.
        
    7. The result is a fully controllable, animatable rim light that is layered on top of your original render. You can change its direction, color, and intensity in real-time within the compositor, providing immense flexibility.