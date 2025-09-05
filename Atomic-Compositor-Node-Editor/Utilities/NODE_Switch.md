- **Editor:** Compositor Node Editor
    
- **Node Group:** Utilities
    
- **Core Function:** Selectively passes one of two input image streams to its output based on a toggleable and animatable switch.
    
- **Key Properties & Settings:**
    
    - Image (Off) ([Socket]): The image data that is passed through when the **Switch** property is unchecked.
        
    - Image (On) ([Socket]): The image data that is passed through when the **Switch** property is checked.
        
    - Switch ([Property]): A checkbox that determines the active input. This property can be keyframed to change over time.
        
    - Image ([Socket]): The resulting image output from either the "On" or "Off" input stream.
        
- **Practical Application:**
    
    - **Molecular (A/B Testing):** The most common use of the **Switch** node is for direct, non-destructive comparison. Instead of muting and unmuting nodes, connect two different "molecules" (e.g., two different **Glare** node settings or two different **Color Balance** adjustments) to the "On" and "Off" inputs. This allows you to instantly flip between the two results in the **Viewer** to decide which approach works better for the shot.
        
    - **Molecular (Version Control):** Use this node to maintain a simple, non-destructive history of your work. Keep your original, approved effect chain plugged into the "Off" socket while you experiment with a new version plugged into the "On" socket. This creates an easily managed "molecule" for iterating on looks without having to rebuild the previous setup if you want to revert.
        
    - **Organic (Animated Effect Bypass):** The true power of this "atom" is realized when its **Switch** property is animated. Imagine an "organism" that creates a complex lens dirt or rain-on-the-lens effect. This effect should only be visible for a certain portion of the animation. By feeding the original clean plate into the "Off" socket and the entire complex effect chain into the "On" socket, you can use two keyframes on the **Switch** property to turn the entire organism on and off precisely when needed. This is far cleaner and more efficient than animating the mix factors of dozens of individual nodes.
        
    - **Organic (Multi-Pass Workflow Switching):** In a professional studio pipeline, you might have different render "organisms" for the same shot, such as a full path-traced version and a faster, baked-lighting version for background elements. The **Switch** node can act as a master control, allowing a compositor to easily swap the entire background element's lighting setup from one system to another, or even switch between a CG background and a matte painting for different parts of a sequence, all managed by a single, animatable control.