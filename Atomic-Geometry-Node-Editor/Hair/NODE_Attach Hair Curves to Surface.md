**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Utility)

**Core Function:** Projects and connects the root points of existing hair curves onto a target surface mesh, establishing a formal attachment relationship.

**Key Properties & Settings:**

- **Geometry (Input):** The set of hair curves that you want to attach.
    
- **Surface (Input):** The mesh geometry that the hair will be attached to. This is a mandatory input.
    
- **Surface UV Map (Input):** The UV map on the surface that will be used to store the attachment location for each hair. This is a mandatory input.
    
- **Snap to Surface (Input):** When enabled, this moves the root of each curve to the closest point on the target surface.
    
- **Align to Surface Normal (Input):** Rotates the base of the curve to align with the normal direction of the surface at the attachment point.
    
- **Surface UV Coordinate (Output):** The 2D UV coordinate of the attachment point for each curve.
    

**Practical Application:**  
This node is essential when you have hair geometry that was created or imported separately from the scalp or skin mesh and you need to formally link them together for further simulation or deformation. For instance, imagine you have an animated rhino model and a separate, static set of fur curves that you want to make follow the rhino's animation.

- **The Goal:** To make a pre-existing, static set of fur curves stick to and deform with an animated rhino mesh.
    
- **The Problem:** The fur curves and the rhino are two independent objects. When the rhino moves, the fur is left behind. You need to tell each hair curve which part of the rhino's surface it "belongs" to.
    
- **The Solution:** The Attach Hair Curves to Surface node creates this relationship.
    
    1. Place the Attach Hair Curves to Surface node in the fur object's node tree.
        
    2. Connect the fur curves to the Geometry input.
        
    3. Use an Object Info node to bring in the animated rhino mesh and connect it to the Surface input. You must also specify the rhino's UV map.
        
    4. Enable Snap to Surface. This will find the closest point on the rhino's skin for each hair root and move it there.
        
    5. Enable Align to Surface Normal to make the hairs point outwards from the skin correctly.
        
    6. The node now stores the attachment information (the UV coordinate of the root) on each hair.
        
    7. You can now follow this up with a Deform Curves on Surface node. This second node will use the attachment information to ensure that as the rhino mesh deforms during its animation, the attached hair curves are carried along with the surface, making the fur stick perfectly.