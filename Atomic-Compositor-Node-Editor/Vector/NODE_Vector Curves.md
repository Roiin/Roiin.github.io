- **Editor:** Compositor Node Editor
- **Node Group:** Vector
    
- **Core Function:** Remaps the individual X, Y, and Z components of an input vector using a graphical curve editor for precise, non-linear adjustments.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket - Input):** The source vector data (e.g., a Normal pass or Speed Vector pass) to be manipulated.
        
    - **Curve Editor (Property):** A graphical interface with separate, color-coded curves for the X (red), Y (green), and Z (blue) components. Points can be added and moved to reshape the input-to-output mapping.
        
    - **Clipping (Property):** Controls how the curve behaves for input values outside the standard 0-1 range. Can be set to Clip to clamp values or Extend to extrapolate the curve.
        
    - **Vector (Socket - Output):** The final, remapped vector after its components have been processed by their respective curves.
        
- **Practical Application:** This node is a powerful tool for creatively modifying vector-based render passes, such as the Speed Vector pass used for motion blur. By precisely adjusting the motion vectors, you can create stylized or exaggerated motion blur effects.
    
    1. Start with a **Render Layers** node that has the **Speed Vector** pass enabled. This pass encodes the motion of pixels between frames as a vector.
        
    2. Connect the Vector output from the render layer into the **Vector Curves** node's Vector input.
        
    3. Feed the output of the **Vector Curves** node into the Speed input of a **Vector Blur** node. The main Image output also feeds into the **Vector Blur** node's Image input.
        
    4. In the **Vector Curves** node, select the X curve (red). Add a point in the middle and drag it upwards, creating a steeper slope. This will amplify any horizontal motion in the scene, causing the horizontal blur to become much longer and more pronounced.
        
    5. Now, select the Y curve (green). Click on the top-right point of the curve and drag it straight down to the bottom-right corner, making the entire curve a flat horizontal line at 0. This effectively nullifies all vertical motion vectors by remapping any input Y value to an output of 0.
        
    6. The result is a highly stylized motion blur effect where all movement is strictly horizontal, regardless of the original 3D motion. This technique allows for artistic control over motion blur that would be impossible to achieve with standard settings, perfect for creating speed-line effects or other non-photorealistic motion graphics.