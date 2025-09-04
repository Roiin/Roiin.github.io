- **Editor:** Geometry Node Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Provides a single, static color value, selectable via an interactive color picker on the node itself.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Color Picker (Property):** An interactive color swatch directly on the node. Clicking it opens the full color selection interface (RGB, HSV, Hex, etc.).
        
    - **Color (Socket - Output):** The selected RGBA (Red, Green, Blue, Alpha) color value.
        
- **Practical Application:** The most direct way to define base colors in the Shader Editor. This can be used to set the exact hue for a faction's banner, the color of a character's eye glow, or to create a simple color parameter that can be easily tweaked within a material group without altering the underlying logic. In Geometry Nodes, it can be used to set a uniform color attribute across a generated mesh.