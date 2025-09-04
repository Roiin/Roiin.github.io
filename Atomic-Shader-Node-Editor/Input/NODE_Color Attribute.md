**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Selects and outputs a specific vertex color layer (Color Attribute) by name, providing its color and alpha channels for use in the shader.

**Key Properties & Settings:**

- **Color Attribute (Property):** The primary control. A dropdown menu that lists all available Color Attributes (vertex color layers) on the object, allowing you to select the desired one by name.
    
- **Color (Output):** Outputs the RGB data from the selected vertex color layer.
    
- **Alpha (Output):** Outputs the alpha channel data from the selected vertex color layer, which is essential for creating painted-on transparency or masks with soft edges.
    

**Practical Application:**  
This node is the modern, preferred method for using painted vertex data to drive a material. It's especially powerful for adding layered details with soft blending. Imagine you need to add a complex tattoo to a **stylized skin** material. The tattoo has specific colors and needs to fade gently into the skin at its edges, not look like a hard-edged sticker.

The problem is how to paint both the color and the soft-edged mask at the same time. The Color Attribute node is the ideal solution.

1. On your character mesh, create a new Color Attribute and name it "TattooData".
    
2. In Vertex Paint mode, you can paint the tattoo's design directly onto the model. By using a brush with a soft falloff, you are simultaneously painting the RGB colors of the tattoo and the Alpha values for its transparency (full strength in the middle, fading to zero at the edges).
    
3. In the Shader Editor, start with your base skin shader. Add a Color Attribute node and select "TattooData" from its dropdown menu.
    
4. Use a Mix Color node to blend the tattoo onto the skin. Plug your base skin color into Socket A and the Color output of the Color Attribute node into Socket B.
    
5. Crucially, connect the Alpha output of the Color Attribute node into the Fac of the Mix Color node.
    
6. The result is a perfectly integrated tattoo. The Color output provides the design, while the Alpha output acts as a precise mask, ensuring the edges blend smoothly and realistically into the underlying skin material.