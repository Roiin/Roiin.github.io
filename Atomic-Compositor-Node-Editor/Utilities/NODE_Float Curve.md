- **Editor:** Compositor Node Editor  
- **Node Group:** Utilities
    
- **Core Function:** Provides an advanced, curve-based interface for remapping a single numerical value (a float). It allows for precise, non-linear control over the relationship between an input value and an output value, similar to an F-Curve in the Graph Editor.
    
- **Key Properties & Settings:**
    
    - **Value (Socket):** The standard numerical (float) input to be remapped.
        
    - **Factor (Socket):** Controls the blend between the original value and the remapped value from the curve.
        
    - **Curve (Property):** The main interface.
        
        - The **X-axis** represents the input value (typically from 0 on the left to 1 on the right).
            
        - The **Y-axis** represents the output value (typically from 0 at the bottom to 1 at the top).
            
        - By adding and moving points on the curve, you can create any relationship between the input and output.
            
- **Practical Application:** This node is an "art direction" tool for numerical data. It replaces a complex chain of Math nodes with a single, intuitive visual editor. It's perfect for adding "feel" and "character" to procedural effects.
    
    - **Molecular (Custom Falloff / Easing):** This is its most common and powerful use. Instead of a linear fade or transition, you can create a custom one.
        
        1. Take the output of a Time node (which goes from 0 to 1).
            
        2. Feed it into a Float Curve.
            
        3. Draw an "S"-shaped curve.
            
        4. The Value output will now animate from 0 to 1 with a smooth ease-in and ease-out. This can be used to drive the Factor of a Mix node for a much more appealing transition than a linear one.
            
    - **Molecular (Fine-Tuning Masks):** This node is often a more intuitive alternative to a Color Ramp for adjusting grayscale masks. By manipulating the curve, you can precisely control the contrast and falloff of a soft mask (like a vignette or a depth matte) in a non-linear way, allowing you to "crush the blacks" or "roll off the highlights" with artistic precision.
        
    - **Organic (Controlling Procedural Animation):** Imagine you want a Noise Texture to control the Size of a Glare effect, but you want the glow to appear very suddenly and intensely only when the noise value is very high.
        
        1. Feed the Noise Texture into the Value input of a Float Curve.
            
        2. In the curve editor, draw a curve that is flat and low along the bottom, and then spikes up sharply at the far right.
            
        3. Feed the Value output into the Size of the Glare node.
            
        4. The result is a flickering glow that has a very specific "character"—it will be subtle or non-existent most of the time, with sudden, intense flashes. This kind of nuanced control is what the Float Curve excels at.