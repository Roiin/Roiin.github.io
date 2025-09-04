**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Provides a powerful and precise way to remap a grayscale value (float) by using a custom curve, offering more nuanced control than a Color Ramp or Math node.

**Key Properties & Settings:**

- **Value (Output):** The final, remapped float value.
    
- **Curve (Property):** The node's primary interface. It's a graph where the horizontal axis (X) represents the input float value (from 0 to 1) and the vertical axis (Y) represents the remapped output value.
    
- **Value (Input):** The socket for the source float or grayscale texture to be adjusted.
    
- **Fac (Input):** A factor to control the overall strength of the node's effect.
    

**Practical Application:**  
This node is the definitive tool for shaping the profile or falloff of a procedural effect with artistic precision. It is the grayscale equivalent of the RGB Curves node. Imagine you are creating a procedural mask for the sheen on a piece of **velvet** fabric using the Facing output of a Layer Weight node.

The problem is that the default linear gradient of the Layer Weight node might be too broad or too harsh for the specific look you want. You need to control the exact "shape" of the falloff—perhaps making it very subtle at first and then flaring up sharply right at the edge. The Float Curve node is the perfect solution.

1. Take the Facing output from a Layer Weight node.
    
2. Connect it to the Value input of a Float Curve node.
    
3. In the curve editor, you can now reshape the linear gradient. To create a sharp falloff, you can create an "ease-in" curve that stays low (black) for most of its length and then curves steeply upwards to white only at the very end.
    
4. Connect the Value output of the Float Curve to the Fac input of a Mix Shader that blends your dark velvet base with a bright sheen shader.
    
5. The result is a highly art-directable velvet sheen. Instead of a simple linear fade, the sheen will now appear exactly according to the custom profile you drew in the Float Curve. This gives you unparalleled control over the subtlety and character of view-dependent effects.