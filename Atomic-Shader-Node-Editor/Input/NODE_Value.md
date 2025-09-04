**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides a single, user-defined numerical value that can be plugged into other nodes, acting as a constant or a central controller.

**Key Properties & Settings:**

- **Value (Property/Output):** A simple numerical field where a floating-point number can be entered. The value entered here is provided at the Value output socket, ready to be connected to any input that accepts a single number (typically a gray socket).
    

**Practical Application:**  
This node is fundamental for creating clean, artist-friendly materials by centralizing control over key attributes. Imagine you are creating a complex procedural **ice** material. The "frostiness" of the ice depends on several factors: the Roughness of the surface, the Scale of a Noise Texture used for the bump map, and the Scale of the Subsurface Scattering.

The problem is that these three properties are located on three different nodes. To make the ice more or less frosty, you have to find and tweak three separate sliders, trying to keep them in balance. This is inefficient and clunky. The Value node is the solution.

1. Add a Value node to your graph and, for clarity, give it a label like "Master Frostiness".
    
2. Connect the Value output of this node to the Roughness input on your Principled BSDF.
    
3. Connect the same Value output to the Scale input of your Noise Texture. You might add a Math node (set to Multiply) in between to make the effect stronger (e.g., multiply the 0-1 value by 50 for the texture scale).
    
4. Connect it to the Scale of your Subsurface Scattering as well.
    
5. Now, instead of hunting for three different sliders, you have a single "Master Frostiness" control. Increasing this one value simultaneously makes the ice rougher, increases the detail of the frosty bump, and adjusts the light scattering, all from one convenient location. This turns a complex network into an intuitive material with a simple, powerful master control.