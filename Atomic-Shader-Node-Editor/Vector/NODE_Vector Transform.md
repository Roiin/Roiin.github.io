**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Transforms a vector, point, or normal from one coordinate system (e.g., World Space, Object Space, Camera Space) to another.

**Key Properties & Settings:**

- **Vector (Input/Output):** Takes a vector as input and outputs the same vector translated into the new coordinate space.
    
- **Type (Property):** Specifies the kind of data being transformed. Point is for location data, Vector is for direction data, and Normal is crucial as it applies a special transformation to ensure normals remain correct under non-uniform scaling.
    
- **Convert From (Property):** The coordinate system of the input vector. Common choices are World, Object, or Camera.
    
- **Convert To (Property):** The target coordinate system you want the vector to be in.
    

**Practical Application:**  
This node is essential for creating "world space" textures that ignore an object's local rotation and scale. This is invaluable for effects that need to be consistent across multiple, different objects. Imagine you have several pieces of rubble from a destroyed wall, and you want to apply a layer of moss that appears to grow consistently down the Z-axis, as if dripping with gravity.

The problem is that if you use standard Object or Generated coordinates, the moss texture will be rotated and scaled differently on each piece of rubble, since each piece has its own unique orientation. This will look unnatural. You need the texture to be mapped from a single, global coordinate system. The Vector Transform node is the solution.

1. Start with a Texture Coordinate node and take its Object output. This gives you a stable coordinate system for each piece of rubble.
    
2. Add a Vector Transform node. Set its Type to Point.
    
3. Set Convert From to Object and Convert To to World.
    
4. Connect the output of the Vector Transform node to the Vector input of your procedural moss texture (e.g., a Noise Texture).
    
5. The result is that the moss texture is no longer mapped based on each object's individual rotation. Instead, it is projected through the entire scene in world space. This means the "drips" in the moss texture will always point straight down the global Z-axis, creating a coherent and believable effect across all the separate pieces of rubble, making them look like they belong in the same environment.