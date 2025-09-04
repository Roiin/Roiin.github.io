**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Remaps a numerical value from an input range to a new output range, effectively stretching, squashing, and offsetting the value.

**Key Properties & Settings:**

- **Result (Output):** The final, remapped value.
    
- **Value (Input):** The input socket for the value or grayscale texture to be remapped.
    
- **From Min / From Max:** These two inputs define the expected range of the incoming value. For most procedural textures like Noise, this is typically 0.0 and 1.0.
    
- **To Min / To Max:** These two inputs define the target range for the output. This is where you set the new desired boundaries for the value.
    
- **Clamp (Property):** When checked, this ensures the output value will never go outside the To Min / To Max range, even if the input value was outside the From Min / From Max range.
    

**Practical Application:**  
This node is an essential utility for adapting the output of one node to the required input range of another. It's the perfect tool for preparing a texture to be used for displacement.

The problem with using a raw Noise Texture (which outputs values from 0 to 1) for displacement is that it will only push the geometry outwards. For a balanced effect where the surface is pushed both inwards and outwards, you need the texture's range to be -1 to 1, with 0 being the "no displacement" mid-point. The Map Range node is the ideal solution.

1. Start with a Noise Texture.
    
2. Connect its Factor output to the Value input of a Map Range node.
    
3. The Noise Texture's range is 0 to 1, so set From Min to 0.0 and From Max to 1.0.
    
4. You want the output range to be -1 to 1, so set To Min to -1.0 and To Max to 1.0.
    
5. Connect the Result of the Map Range node to a Displacement node's Height input. You will also need to set the Midlevel on the Displacement node to 0.0 to match this new range.
    
6. The result is a perfectly balanced displacement. The original black (0) areas of the noise are now mapped to -1, pushing the surface inwards. The original white (1) areas are mapped to 1, pushing outwards. And the original mid-gray (0.5) is now mapped to 0, which becomes the neutral, non-displaced mid-point. This creates a much more natural and controllable displacement effect.