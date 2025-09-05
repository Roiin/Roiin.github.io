- **Editor:** Compositor Node Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Provides a visually animatable factor (typically 0 to 1) over a specified frame range, allowing for complex, non-linear timing and animation to be controlled by drawing a curve. It's a keyframe-free way to create sophisticated timing.
    
- **Key Properties & Settings:**
    
    - **Start Frame (Property):** The frame number where the time effect begins. This marks the left side (X=0) of the curve editor.
        
    - **End Frame (Property):** The frame number where the time effect ends. This marks the right side (X=1) of the curve editor.
        
    - **Curve (Property):** A standard curve widget where the X-axis represents the frame range (from Start to End) and the Y-axis represents the output Factor. Allows for custom easing, holds (flat lines), and complex timing adjustments using Bézier handles.
        
    - **Factor (Socket):** Outputs the numerical value from the curve's Y-axis corresponding to the current frame on the X-axis.
        
- **Practical Application:** This node replaces the need for manual keyframing for a single value, giving you a much more intuitive and visual way to control animations over time.
    
    - **Molecular (Art-Directed Fades and Transitions):** Instead of a linear fade, you can create a much more appealing one.
        
        1. Set the Start Frame and End Frame for your transition.
            
        2. Draw an "S"-shaped curve in the Curve widget.
            
        3. Feed the Factor output into the Factor of a Mix node that is blending two video clips.
            
        4. The result is a professional-looking transition that starts slow, accelerates through the middle, and then eases to a gentle stop, all controlled visually by the curve's shape.
            
    - **Molecular (Ease-In/Ease-Out Motion Graphics):** To animate a title sliding onto the screen with style.
        
        1. Use the Factor output to drive a Map Range node, mapping the 0-1 range to the desired screen coordinates (e.g., from Y= -500 to Y=0).
            
        2. Feed this result into the Y-position of a Transform node affecting your title text.
            
        3. By adjusting the curve handles, you can make the title ease into its final position, hold for a moment (a flat section of the curve), and then zip off-screen with a different timing.
            
    - **Organic (Orchestrating Effect Sequences):** This node shines when you use multiple instances to time a sequence of events. Imagine a "power up" effect:
        
        1. **Curve 1 (Glow):** A slow, steady ramp from 0 to 1 over 60 frames. This controls the Size of a Glare node to make an object slowly start glowing.
            
        2. **Curve 2 (Shake):** A curve that is flat at 0 until frame 50, then quickly spikes up and back down. This drives the Distance of a Displace node, causing a violent shake only at the peak of the glow.
            
        3. **Curve 3 (Flash):** A curve that is 0 everywhere except for a single-frame spike to 1 at frame 60. This controls the Factor of a Mix node blending in a pure white color, creating a final flash.  
            Using these three nodes, you have choreographed a complex, multi-stage effect with purely visual and easily adjustable timing controls.