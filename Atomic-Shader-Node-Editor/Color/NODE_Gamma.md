**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Color

**Core Function:** Adjusts the luminance of a color or texture by applying a power-law (gamma) correction, which primarily affects the mid-tones without blowing out the highlights or crushing the blacks.

**Key Properties & Settings:**

- **Color (Output):** The final, gamma-corrected color.
    
- **Gamma (Input):** The correction factor. A value of 1.0 makes no change. Values greater than 1.0 lighten the mid-tones, while values less than 1.0 darken the mid-tones.
    
- **Color (Input):** The socket for the source color or texture to be adjusted.
    

**Practical Application:**  
This node is excellent for subtly reshaping the falloff of procedural textures to make them feel more natural. Imagine you are creating a procedural mask for grime or light **rust** accumulation using a Noise Texture.

The problem is that the raw output of a Noise Texture often has a very linear, uniform gradient between its dark and light values. This can make the transition from the "clean" to the "rusted" area look too even and artificial. You need to control the curve of this transition. The Gamma node is the perfect solution for this.

1. Take the grayscale Factor output from your Noise Texture.
    
2. Before using it as a mask, pass it through a Gamma node.
    
3. By setting the Gamma value to a number greater than 1.0 (e.g., 2.0), you will push the mid-gray values of the noise up towards white. This tightens the mask, concentrating the rust effect only in the darkest core areas of the noise pattern and creating a sharper, more defined falloff.
    
4. Conversely, setting the Gamma below 1.0 (e.g., 0.5) will push the mid-grays towards black, expanding the rusted area and making the transition softer and more gradual.
    
5. This provides fine control over the falloff of the procedural rust, allowing you to tune how the effect "creeps" into the clean areas with more subtlety than a simple contrast adjustment.