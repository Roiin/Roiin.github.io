**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a volumetric density field based on the positions of vertices or particles from a specified source object.

**Key Properties & Settings:**

- **Density (Output):** The primary output, providing a volumetric density value. This is typically connected to the Density or Emission Strength input of a Principled Volume shader.
    
- **Color (Output):** Provides a color for the volume, derived from a specified attribute of the source points (e.g., particle age or vertex color).
    
- **Point Data (Property):** The core control that determines the source of the points.
    
    - **Particle System:** Uses the location of each particle from a particle system.
        
    - **Object Vertices:** Uses the location of each vertex from a mesh.
        
- **Object (Property):-** A selector to choose which object in the scene will provide the points.
    
- **Radius (Property):** Controls the size or influence of each individual point, creating larger or smaller volumetric spheres around each source point.
    
- **Resolution (Property):** Sets the resolution of the internal voxel grid used to calculate the density. Higher values capture more detail but use more memory.
    
- **Color Source (Property):** When using particles, this allows you to color the resulting volume based on particle properties like Particle Age or Particle Speed.
    

**Practical Application:**  
This node is perfect for creating "field" or "aura" effects around objects without complex simulations. Imagine you want to create a glowing energy field or a magical mist that emanates directly from a character's body.

The problem is that a standard volumetric object is a simple shape like a cube, and making it conform to a complex character mesh is difficult. You need the volume to be intrinsically linked to the character's geometry. The Point Density node is the solution.

1. Create a cube object that completely encloses your character. This cube will be your "volume domain."
    
2. Assign a new material to this cube. In the Shader Editor, delete the Principled BSDF and add a Principled Volume shader, connecting it to the Volume input of the Material Output.
    
3. Add a Point Density node. Set its Point Data to Object Vertices and use the eyedropper to select your character model as the Object.
    
4. Connect the Density output of the Point Density node to the Density input of the Principled Volume shader. To make it glow, you could also connect Density to the Emission Strength.
    
5. Adjust the Radius to control how far the volumetric mist extends from the surface of the character's mesh.
    
6. The result is a volumetric mist that is no longer a simple cube. It now exists only in the areas immediately surrounding the character's vertices, creating a perfect, form-fitting aura that will follow the character's animation precisely.