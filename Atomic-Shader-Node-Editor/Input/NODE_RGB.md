**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides a specific, user-selected color value for use within the shader tree.

**Key Properties & Settings:**

- **Color (Output / Property):** The primary user interface and output of the node. It is a standard color swatch that allows you to visually pick a color or enter its precise RGBA, HSV, or Hexadecimal values. This single output can be connected to multiple other nodes.
    

**Practical Application:**  
This node acts as a central color controller, which is vital for keeping complex materials organized and easy to edit. Imagine you are creating a stylized **ice** material that needs a very specific shade of blue. This blue will be used for the base color, the subsurface scattering color, and a faint emission glow to make it look magical.

The problem is that if you set this specific blue on three different nodes (Principled BSDF, Subsurface Scattering, Emission), and later decide to change the hue, you have to find and manually update all three color swatches. This is inefficient and risks creating color inconsistencies. The RGB node is the solution.

1. Add a single RGB Node to your graph and select your desired shade of magical blue.
    
2. Connect the Color output of this one RGB Node to the Base Color input of your main shader, the Subsurface Color input, and the Color input of an Emission shader.
    
3. Now, this RGB Node acts as a master "color variable." If you want to change the ice from a light cyan to a deep arctic blue, you only need to adjust the color in this one place. The change will instantly and consistently propagate to every part of the material, making experimentation and art direction significantly faster and more reliable.