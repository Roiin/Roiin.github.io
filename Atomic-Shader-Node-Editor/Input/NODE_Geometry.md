**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Provides access to the mesh's fundamental geometric properties like surface position, normal direction, and curvature at the point of shading.

**Key Properties & Settings:**

- **Pointiness [Cycles Only]:** The most powerful output for procedural texturing. It calculates the curvature of the surface, producing a grayscale map where bright white represents sharp convex edges (outer corners) and black represents concave areas (crevices).
    
- **Normal:** The shading normal vector. This is the normal used for lighting calculations and includes the effects of smooth shading and any connected bump/normal maps.
    
- **True Normal:** The raw geometric normal of the polygon face itself, ignoring smooth shading. It gives a faceted look.
    
- **Random per Island [Cycles Only]:** Assigns a unique, random grayscale value to each disconnected "island" of a single mesh object.
    
- **Backfacing:** Outputs white for the back side of a polygon's face and black for the front. Essential for creating two-sided materials.
    

**Practical Application:**  
The Pointiness output is the industry standard for creating procedural edge wear. Imagine you are creating a material for a painted metal container that has been scraped and weathered, exposing the bare metal on its sharpest edges.

The problem is how to procedurally create a mask that isolates only these convex edges. The Geometry node is the solution.

1. Create two Principled BSDF shaders: one for the outer "Paint" layer and another for the "Bare Metal" underneath.
    
2. Use a Mix Shader to blend between them, with the "Bare Metal" shader in the bottom slot.
    
3. Connect the Pointiness output of the Geometry node into the Fac input of the Mix Shader.
    
4. The default Pointiness output is subtle, so insert a ColorRamp node between the Geometry node and the Mix Shader to "crush" the values. By sliding the black and white handles of the ColorRamp closer together, you can create a high-contrast mask that is pure white on the sharpest edges and black everywhere else.
    
5. This mask will now perfectly reveal the "Bare Metal" shader on the worn edges, creating a highly realistic and fully procedural wear-and-tear effect.