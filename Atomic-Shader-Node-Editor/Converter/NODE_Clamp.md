**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Constrains an input value, forcing it to stay within a user-defined minimum and maximum range.

**Key Properties & Settings:**

- **Result (Output)::** The final, clamped value.
    
- **Value (Input):** The input socket for the value or texture to be clamped.
    
- **Min (Input):** The lower boundary. Any input value below this number will be raised to this number.
    
- **Max (Input):** The upper boundary. Any input value above this number will be lowered to this number.
    
- **Clamp Type (Property):** Min Max is the standard mode. Range is a special case that allows the Min value to be higher than the Max, effectively inverting the clamp range.
    

**Practical Application:**  
This node is an essential utility for preventing unwanted or non-physical values in a procedural shader. Imagine you are creating a material with a "shininess" control that is driven by a Noise Texture. This control should only affect the Roughness of your Principled BSDF.

The problem is that a Noise Texture outputs values across the full 0-to-1 range. This means some parts of your material could become perfectly mirror-like (Roughness = 0.0), which might be unrealistic, and other parts could become perfectly diffuse (Roughness = 1.0), which might be too dull. You need the roughness to vary, but only within a specific, controlled range (e.g., between 0.1 and 0.4). The Clamp node is the solution.

1. Take the Factor output of your Noise Texture.
    
2. Connect it to the Value input of a Clamp node.
    
3. Set the Min value to 0.1 and the Max value to 0.4.
    
4. Connect the Result of the Clamp node to the Roughness input of your Principled BSDF.
    
5. Now, even though the Noise Texture is generating values from 0 to 1, the Clamp node will "catch" them and force them into your desired range. Any value below 0.1 will be raised to 0.1, and any value above 0.4 will be lowered to 0.4. This ensures your material's shininess has natural-looking variation without ever reaching unrealistic extremes, giving you precise artistic control over the final result.