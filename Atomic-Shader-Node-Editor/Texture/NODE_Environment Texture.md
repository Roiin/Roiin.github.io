**Editor:** Shader Editor (World Context)  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Loads an image file, typically a 360° High Dynamic Range Image (HDRI), to be used as the scene's environmental background and primary source of realistic light and reflections.

**Key Properties & Settings:**

- **Color (Output):** The primary output. It provides the color data from the loaded image and should be connected to the Color input of a Background shader in the world node tree.
    
- **Image (Property):** The data block where you open and select your image file.
    
- **Projection Method (Property):** The most critical setting for HDRIs. It tells Blender how to wrap the 2D image into a 3D sphere. Equirectangular is the standard for most 360° HDRIs.
    
- **Vector (Input):** Accepts a vector to control the orientation of the environment map. This is typically connected to a Mapping node to allow you to rotate the HDRI, effectively changing the direction of the sunlight and reflections.
    
- **Color Space (Property):** Specifies how the color data in the image should be interpreted. For most HDRIs (.hdr, .exr), the default Linear is correct. For standard images (JPG, PNG), it's typically sRGB.
    

**Practical Application:**  
This node is the single most effective tool for achieving photorealistic lighting and reflections. Imagine you have modeled a vehicle with a glossy car paint finish and chrome details. You place it in an empty scene and render it.

The problem is that the car looks completely fake, like a toy floating in a black void. The chrome doesn't look like metal because it has nothing to reflect, and the lighting is flat and boring. The Environment Texture node is the definitive solution.

1. Switch to the Shader Editor's "World" context.
    
2. Add an Environment Texture node and load an HDRI of a real-world location, for example, a city street or an open field at sunset.
    
3. Connect the Color output of this node to the Color input of the Background shader (which is connected to the World Output).
    
4. Instantly, the entire scene is lit by the complex, nuanced light of the real-world photo. Most importantly, the chrome bumpers and glossy paint of the car now show crisp, detailed reflections of the buildings, sky, and trees from the HDRI. This single node provides both the global illumination and the reflections necessary to make the material feel grounded and physically present in a realistic environment.