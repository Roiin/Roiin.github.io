**Editor:** Shader Editor (Light Context)  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Color

**Core Function:** Provides artistic control over the rate at which a light source's intensity diminishes with distance, allowing for non-physically-based falloff effects.

**Key Properties & Settings:**

- **Quadratic (Output):** This output represents the physically correct, real-world behavior of light, where intensity decreases with the square of the distance. For realistic lighting, this should be used.
    
- **Linear (Output):** This output creates a much slower, linear decrease in intensity. Light will travel further before fading, which is useful for stylized or gameplay-focused lighting where you need to illuminate a larger area more evenly.
    
- -**Constant (Output):** This output completely eliminates falloff. The light will have the same intensity regardless of distance, similar to a Sun light.
    
- **Strength (Input):** The initial intensity of the light source before the falloff calculation is applied. This is typically connected to an Emission shader's Strength input.
    
- **Smooth (Input):** A value that softens the light's intensity close to the source, which can help reduce harsh highlights and noise.
    

**Practical Application:**  
This node is primarily used in a light's shader tree to achieve specific artistic or technical lighting goals that defy real-world physics. Imagine you are lighting a scene for a video game or a stylized animation, and you need a key light to illuminate a character evenly, even if they move slightly further away from the source.

The problem is that a real-world light (Quadratic falloff) will cause the character's illumination to change noticeably with even small movements, which can be distracting. You need the light to have a more consistent, less sensitive intensity over a specific area. The Light Falloff node is the solution.

1. Select a Point Light. In its Object Data Properties, enable Use Nodes.
    
2. The default light shader has a value (e.g., 100) plugged into the Emission shader's Strength. Add a Light Falloff node.
    
3. Connect the light's original strength value into the Strength input of the Light Falloff node.
    
4. Instead of using the default Quadratic output, connect the Linear output to the Emission shader's Strength input.
    
5. The result is a light source that now has a much softer, more gradual, and artist-friendly falloff. The character can move more freely within the light's range without drastic changes in brightness, giving you more stable and controllable lighting for non-photorealistic applications.