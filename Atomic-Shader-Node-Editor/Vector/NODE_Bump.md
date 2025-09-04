**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Fakes the appearance of fine surface detail and relief by manipulating how light interacts with the surface, without altering the object's actual geometry.

**Key Properties & Settings:**

- **Normal (Output):** The primary output. This provides the modified normal vector and must be connected to the Normal input of any BSDF shader (e.g., Principled BSDF).
    
- **Height (Input):** The most critical input. This socket accepts a grayscale texture (a "height map") where white values are interpreted as high points and black values as low points.
    
- **Strength (Input):** A simple multiplier (from 0 to 1) that controls the overall intensity of the bump effect.
    
- **Distance (Input):** Controls the virtual depth of the bump effect in scene units. This is the main control for how "deep" the bumps appear. Small values are typically more realistic.
    
- **Invert (Property):** A checkbox that inverts the height map, causing low points (black) to be treated as high points and vice-versa.
    

**Practical Application:**  
This node is fundamental for adding a sense of physical texture to an otherwise perfectly smooth surface. It is the ideal tool for creating the tactile feel of **wood grain**.

The problem is that when you apply a wood grain texture to a surface, it looks flat, like a photograph laminated onto a board. Real wood has a physical texture; the darker pores of the grain are slightly recessed. You need to simulate this relief. The Bump node is the solution.

1. Start with your Principled BSDF and the procedural or image-based texture that defines your wood grain pattern.
    
2. Take the grayscale version of this wood grain texture (you can use a ColorRamp to isolate it or simply plug the color output directly) and connect it to the Height input of the Bump node.
    
3. Connect the Normal output of the Bump node to the Normal input of your Principled BSDF.
    
4. The result is immediate. The lighting on the surface will now behave as if the darker parts of the grain are recessed and the lighter parts are raised. The surface will catch highlights and cast tiny shadows along the grain lines, giving the material a convincing, physical texture and transforming it from a flat image into a believable wood surface, all without adding a single polygon.