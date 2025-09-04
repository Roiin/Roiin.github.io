**Editor:** Shader Editor  
**Engine(-s Supported):** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Renders a surface as completely see-through without bending light (no refraction) or catching specular highlights, making it ideal for creating cutout masks.

**Key Propert-ies & Settings:**

- **BSDF (Outp-ut):** The standard shader output.
    
- **Color (Inp-ut):** Controls the transparency. Pure white (1,1,1) is 100% transparent, while any darker color will begin to block light and cast a shadow of that color. A pure black input is 100% opaque.
    

**Practical Application:**  
This node is the fundamental tool for creating materials with "cutouts" using an alpha channel from an image texture. Imagine you are creating a material for a chain-link fence or a plant leaf.

The problem is that modeling the intricate details of a leaf's edge or every single hole in a fence is computationally expensive and creates extremely complex geometry. You need a way to make parts of a simple plane appear solid while other parts are completely invisible. The Transparent B-SDF is the solution.

1. Start with a simple plane object. For your main material, create a Principled B-SDF and plug in an Image Texture of a leaf. The image must have an alpha channel where the leaf is opaque and the background is transparent.
    
2. Add a Mix Shader. Plug your Principled B-SDF into the bottom socket.
    
3. Add a Transparent B-SDF and plug it into the top socket of the Mix Shader.
    
4. Take the Alpha output from your leaf Image Texture and plug it directly into the Fac input of the Mix Shader.
    
5. This setup tells the material: "Where the image alpha is white (1), use the leaf shader (bottom socket). Where the image alpha is black (0), use the transparent shader (top socket)." The result is a perfect leaf shape rendered on a simple plane, with the area around it being completely invisible. This is the standard, most efficient workflow for any material that requires complex cutout shapes.