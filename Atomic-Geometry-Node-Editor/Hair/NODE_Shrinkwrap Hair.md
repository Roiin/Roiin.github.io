**Editor:** Geometry Nodes Editor

- **Node Group:** Hair Nodes (Deformation)
    

**Core Function:** Conforms hair curves to the shape of a target surface mesh, effectively "draping" or "projecting" them onto it.

**Key Properties & Settings:**

- **Surface (Input):** The mesh geometry that the hair curves will be wrapped onto.
    
- **Factor (Input):** A global control for the strength of the shrinkwrap effect. At 1.0, the curves are fully wrapped to the surface.
    
- **Offset Distance (Input):** A float value that defines a distance to hold the curves away from the target surface after wrapping. This is useful for preventing the hair from clipping through the mesh.
    
- **Above Surface (Input):** A secondary factor that allows you to apply a different shrinkwrap effect for points that are above the target surface, useful for containing hair within a volume.
    
- **Lock Roots (Input):** When enabled, this prevents the root of each hair from being moved by the shrinkwrap operation.
    

**Practical Application:**  
This node is essential for making hair interact with other objects, such as conforming a long hairstyle to the shape of a character's shoulders or making fur lie flat against clothing. Imagine a long-haired animal, like a collie, that is wearing a collar.

- **The Goal:** To make the collie's long neck fur lie flat underneath its collar, instead of clipping through it.
    
- **The Problem:** The hair is generated from the dog's skin and flows outwards. A separate collar mesh placed around the neck will cause the long hair to intersect and poke through it, which looks physically incorrect.
    
- **The Solution:** Use the Shrinkwrap Hair Curves node to force the hair down onto the surface of the collar.
    
    1. Place the Shrinkwrap Hair Curves node after the initial hair generation and grooming.
        
    2. Connect the collar's geometry to the Surface input of the node.
        
    3. You can use a weight map to drive the Factor, so that the shrinkwrap effect is strongest only on the hair that is directly under the collar.
        
    4. Set a small Offset Distance to ensure the hair lies just on top of the collar's surface without intersecting it.
        

As the Factor is increased, the hair curves under the collar's influence will be projected down onto its surface. This makes the fur conform realistically to the accessory, tucking it underneath and resolving the ugly clipping issue.