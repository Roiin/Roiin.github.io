- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Binds curves (like hair or fur) to a deforming surface mesh, making them stick to and move with the surface as it animates. It works by tracking the position of UV coordinates from the mesh's original state to its final, deformed state. **Crucially, this node relies on a specific setup in the curve object's Object Data Properties panel and is not a self-contained operation.**
    
- **Key Properties & Settings:**
    
    - **Implicit Setup (Required):**
        
        1. The node must be on a Curve object.
            
        2. In the Object Data Properties for the curve object, a target mesh must be set in the Curves Surface panel.
            
        3. A UV Map from that target mesh must also be selected in the same panel.
            
        4. The curves must have a special surface_uv_coordinate attribute that stores the root position of each curve on the target UV map. (This is often generated automatically when creating hair particle systems).
            
    - **Curves (Socket - Input):** The source curves (e.g., hair strands) to be deformed.
        
    - **Curves (Socket - Output):** The deformed curves, now adhering to the animated surface.
        
    - **Important Note:** To function correctly with a Subdivision Surface modifier on the target mesh, the modifier's UV Smooth option should be set to 'None'.
        
- **Practical Application:** This node is the key to creating realistic hair and fur on an animated character, like a lion.
    
    1. **The Setup:** You have a lion model with a UV map. You create a full groom of hair curves for its mane. In the Object Data Properties of the mane (the curve object), you set the lion's body mesh as the Surface and select its UV Map.
        
    2. **The Problem:** You then rig and animate the lion. As its neck turns and its shoulders move, the skin stretches and deforms, but the hair strands of the mane remain rigid and either detach from the skin or intersect with the body.
        
    3. **The Solution:** You add the Deform Curves on Surface node into the mane's Geometry Nodes tree.
        
    4. Now, when the animation plays, the node performs a complex calculation for each hair:
        
        - It knows the hair's root is at, for example, UV coordinate (0.5, 0.7).
            
        - It looks at the original, non-deformed lion mesh and finds where (0.5, 0.7) was.
            
        - It looks at the new, animated lion mesh and finds where (0.5, 0.7) has moved to.
            
        - It calculates the difference in position and rotation and applies it to the entire hair curve.
            
    5. The result is a mane that is perfectly "stuck" to the deforming skin. The hairs slide, stretch, and compress realistically with the lion's movements, creating a believable and dynamic animation.