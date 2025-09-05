- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Applies a non-linear brightness adjustment (gamma correction) to an image. This primarily affects the mid-tones, allowing you to brighten or darken the image's middle range of values without clipping the pure blacks or pure whites.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Gamma (Socket):** The correction value. A value greater than 1.0 will lighten the mid-tones. A value less than 1.0 will darken them. A value of 1.0 makes no change. The operation is an exponential curve (color ^ (1/gamma)), which is what gives it the non-linear behavior.
        
- **Practical Application:** The Gamma node is a staple for both precise tonal adjustments and critical technical color space conversions.
    
    - **Molecular (Midtone Brightness Control):** This is its most common artistic use. If your render is generally well-exposed but the shadowy areas are too dark and lack detail, using the Brightness or Exposure nodes would risk blowing out your highlights. Instead, using a Gamma node with a value like 1.2 or 1.5 will "lift" the mid-tones and reveal detail in the shadows while having a much gentler effect on the already-bright areas.
        
    - **Molecular (Technical Color Space Conversion):** This is a critical technical function. Most standard images (like JPGs and PNGs) are saved in the sRGB color space, which has a gamma of ~2.2 applied to it. For physically correct compositing operations (like adding light), you need to work in Linear space. The "molecule" to correctly process an sRGB image is:
        
        1. Image Node (your sRGB image) -> Gamma Node (set to 2.2) to convert to Linear.
            
        2. Perform your Mix (Add) or Multiply operations here.
            
        3. Pipe the result into a final Gamma Node (set to 1.0 / 2.2, which is ~0.45) to convert back from Linear to sRGB for viewing.
            
    - **Organic (Controlling Glow Falloff):** When creating a bloom or glow effect (by isolating highlights, blurring them, and adding them back), the falloff can look very uniform and digital.
        
        1. After blurring your highlights but before you Add them back to the main image, insert a Gamma node.
            
        2. By changing the Gamma value, you can artistically control the shape of the glow. A value > 1.0 will broaden the glow and give it a softer, more atmospheric falloff. A value < 1.0 will tighten and concentrate the glow, making it feel more intense and focused. This gives you direct control over the "character" of your bloom.
            
    - **Organic (Faking a Soft/Diffused Look):** To make an object look softer, as if light is scattering through it (a cheap Subsurface Scattering effect):
        
        1. Isolate your object with a mask.
            
        2. Blur the isolated object's colors slightly.
            
        3. Use a Gamma node on this blurred version to brighten it significantly (e.g., value of 2.0).
            
        4. Use a Mix node set to Screen or Add to blend this bright, blurry version back over the original object with a low factor. The gamma adjustment creates a soft, internal "glow" that mimics the look of diffuse, scattered light.