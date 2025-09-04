**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Shader

**Core Function:** Creates a non-photorealistic, cel-shaded look by quantizing light and shadow into distinct, hard-edged bands, mimicking a cartoon or anime art style.

**Key Properties & Settings:**

- **Component (Property):** The node's primary mode switch.
    
    - **Diffuse:** Creates the main color shading bands. It determines where the object is in light versus in shadow, creating the core cel-shaded effect.
        
    - **Glossy:** Creates a sharp, specular highlight band, independent of the diffuse shading. This is used for the classic shiny spot on cartoon eyes or hair.
        
- **Size (Input):** Controls the threshold for the light/shadow transition. For a Diffuse Toon, a smaller Size results in a larger shadow area. For a Glossy Toon, a smaller Size results in a smaller, tighter highlight.
    
- **Smooth (Input):** Controls the softness of the edge between the bands. A value of 0.0 creates a razor-sharp, classic cartoon line. Higher values create a softer, more feathered gradient.
    
- **BSDF (Output):** The standard shader output.
    

**Practical Application:**  
This node is the cornerstone of the "cel-shading" or anime look, and is perfectly suited for creating **stylized skin** on a cartoon character.

The problem is that a photorealistic shader like the Principled BSDF creates soft, continuous gradients between light and shadow, which looks out of place in a stylized context. You need flat regions of color for light and shadow, and often a separate, sharp highlight. The Toon BSDF is designed to do exactly this.

1. To create the base shading, add a Toon BSDF and set its Component to Diffuse. Connect your character's base skin color to its Color input. Set the Size to around 0.5 and the Smooth to 0.01 (a tiny bit of smoothing helps with anti-aliasing). This immediately creates the main two-tone shading effect.
    
2. To add the characteristic specular highlight, add a second Toon BSDF and set its Component to Glossy. Set its Color to white. Set the Size to a small value like 0.1 and Smooth to 0 to create a small, sharp dot.
    
3. Combine these two shaders using an Add Shader node. Plug the Diffuse Toon shader into the top input and the Glossy Toon shader into the bottom.
    
4. The result is a complete, classic cartoon material. You have the main skin color with a hard shadow line, and layered on top is an independent, sharp white highlight, perfectly capturing the non-photorealistic aesthetic.