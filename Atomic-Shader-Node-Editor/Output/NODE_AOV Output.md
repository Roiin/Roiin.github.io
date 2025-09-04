**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Output

**Core Function:** Channels specific data (like a color, mask, or value) from inside a material into its own separate render pass for use in compositing or debugging.

**Key Properties & Settings:**

- **Name:** The most critical setting. This text field must exactly match the name of a "Shader AOV" pass created beforehand in the View Layer Properties panel. This links the node to the desired output pass.
    
- **Color (Input):** Used to output three-channel data, such as a specific color map, a normal map, or position data, to its own render pass.
    
- **Value (Input):** Used to output single-channel (grayscale) data, such as a roughness map, a metallic mask, or a procedural grime mask.
    

**Practical Application:**  
This node is an essential tool for professional post-production workflows, saving immense amounts of time. Imagine you have created a complex material for a piece of machinery, using a procedural mask to generate **rust**. After a long render, you decide the rust needs to be a slightly different color.

The problem is that re-rendering the entire image just to tweak a color is extremely inefficient. You need a way to isolate the rust so you can adjust it after the render is finished. The AOV Output node is the solution.

1. First, go to the View Layer Properties tab, open the Passes section, and find the Shader AOV panel. Add a new AOV and name it "RustMask".
    
2. In your material, locate the black-and-white procedural texture that you are using as the mask to mix between painted metal and rust.
    
3. Add an AOV Output node. In its Name field, type "RustMask" to match the pass you just created.
    
4. Connect your black-and-white rust mask into the Value input of this AOV Output node.
    
5. Now, when you render, Blender will output your normal beauty image and a separate, black-and-white image of just the rust mask. In the Compositor (or an external program like Photoshop), you can load the main render and use the "RustMask" pass to precisely select only the rusted areas and adjust their color, brightness, or contrast non-destructively, saving you from having to re-render the entire scene.