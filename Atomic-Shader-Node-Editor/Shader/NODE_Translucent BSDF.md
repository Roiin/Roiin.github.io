**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Creates a simple, single-sided translucent material that allows light to pass through and scatter diffusely, but does not provide clear refraction like glass.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **Color (Input):** Defines the color of the material itself and tints the light that scatters through it from behind.
    
- **Normal (Input):** Socket for connecting bump or normal maps to add surface detail.
    

**Practical Application:**  
This node is ideal for thin, single-sided objects that need to be lit from behind, such as paper lampshades, thin curtains, or plant leaves.

Imagine you are modeling a paper lantern or a fabric lampshade with a light bulb inside. The problem is that if you use a standard Diffuse BSDF, the lampshade material will look solid and opaque. The light from the bulb inside will be completely blocked, and the shade itself will remain dark, which is completely unrealistic. The Translucent BSDF is the solution.

1. Instead of a Diffuse BSDF, use a Translucent BSDF for the lampshade's material.
    
2. Set its Color to a slightly off-white or cream color to simulate paper or fabric.
    
3. Now, when a light source is placed inside the lampshade model, the Translucent BSDF allows the light to pass through the geometry. The material itself will catch the light and glow softly, illuminating its own surface. This simple setup perfectly mimics the effect of a real lampshade, creating a warm, scattered glow that a purely opaque shader could never achieve.