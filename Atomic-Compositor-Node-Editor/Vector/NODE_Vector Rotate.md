- **Editor:** Compositor Node Editor
- **Node Group:** Vector
    
- **Core Function:** Rotates an input vector around a specified center point and axis, allowing for the transformation of vector-based render passes.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket - Input):** The source vector data to be rotated, typically a Normal or Position pass.
        
    - **Center (Socket - Input):** The pivot point in 3D space for the rotation. The default of (0,0,0) rotates the vectors around the world origin.
        
    - **Axis (Socket - Input):** A vector that defines the axis of rotation when Type is set to Axis Angle.
        
    - **Angle (Socket - Input):** A float value defining the angle of rotation in radians.
        
    - **Rotation (Socket - Input):** A vector defining the Euler rotation angles when Type is set to Euler.
        
    - **Type (Property):** Sets the method of rotation. Z Axis is common for 2D-like rotation, while Euler or Axis Angle provide full 3D control.
        
    - **Invert (Property):** Reverses the direction of the rotation.
        
    - **Vector (Socket - Output):** The final, rotated vector.
        
- **Practical Application:** This node is invaluable for creating advanced relighting effects, such as animating a light source spinning around a static object directly in the compositor, saving the need for a full 3D re-render.
    
    1. Start with a **Render Layers** node that has the object's **Normal** pass available.
        
    2. Connect the Normal output into the Vector input of the **Vector Rotate** node. Set the Type to Z Axis to create a simple rotation around the axis pointing out of the screen.
        
    3. To animate the rotation, you can keyframe the Angle input or use a driver. A simple driver like #frame * 0.1 will cause the rotation angle to increase with every frame.
        
    4. Next, add a **Normal** node (the one for relighting, not the pass). Set its Normal Direction sphere to a fixed direction, for example, pointing straight from the right side.
        
    5. Connect the Vector output of the **Vector Rotate** node into the Normal input of this **Normal** node.
        
    6. The Dot output of the **Normal** node now produces a dynamic lighting mask. As the driver on the **Vector Rotate** node animates the angle, the rotated normals will change their alignment with the fixed light direction, causing the white "lit" area of the mask to sweep across the object's surface.
        
    7. Use this animated Dot output as the Factor for a **Color Balance** node applied to your main beauty pass. Now, as you play the animation, the object will appear to have a light spinning around it, all generated procedurally within the compositor.