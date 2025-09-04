**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Moves the points of hair curves in a specified direction, or along the surface normals of a separate guide mesh.

**Key Properties & Settings:**

- **Factor (Input):** A global multiplier that scales the overall strength of the displacement effect.
    
- **Displace Vector (Input):** A vector that defines a uniform direction and magnitude for the displacement. All affected hair points will be moved by this vector.
    
- **Surface Normal Displacement (Input):** A float value that controls how far the hair points are pushed along the normals of a separate Surface mesh.
    
- **Surface (Input):** An input for a guide mesh. The normals of this mesh are used as the displacement direction when Surface Normal Displacement is active.
    
- **Shape (Input):** A falloff control that modifies the displacement's strength along the length of each hair strand, from root to tip.
    

**Practical Application:**  
This node is excellent for art-directing the flow of fur by using an invisible "guide" or "force field" mesh. Imagine you are styling the fur on a rhino, and you want the hair on its back to bristle straight up, while the hair on its sides lies flat.

- **The Goal:** To create a "mohawk" or bristling ridge of fur along the rhino's spine.
    
- **The Problem:** The initial fur will likely follow the normals of the rhino's skin, pointing outwards in all directions. You need a way to override this direction for a specific patch of fur and force it to point "up" in world space.
    
- **The Solution:** Use an invisible guide surface to control the displacement.
    
    1. Start with your rhino model and its generated hair curves.
        
    2. Create a separate, simple mesh, like a thin, flat plane. Position this plane just above the rhino's back, and make sure its normals are pointing straight up. This will be your guide surface.
        
    3. On your hair curves, add a Displace Hair Curves node.
        
    4. Connect your new guide plane to the Surface input of the node.
        
    5. Increase the Surface Normal Displacement value. The hair underneath the plane will now be pushed upwards, following the normals of the guide plane instead of the rhino's skin.
        
    6. You can use a weight map on the rhino's skin to drive the Factor of the displacement, ensuring a smooth blend between the bristling fur on the back and the normal fur on the sides.
        

This technique provides a powerful way to "sculpt" the hairstyle of a creature by using the shape and normals of a non-rendering guide object to push the hair into a desired form.