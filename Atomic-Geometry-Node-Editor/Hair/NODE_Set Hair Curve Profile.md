**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Write)

**Core Function:** Sets the per-point radius attribute on hair curves, typically using a curve falloff to define a tapered or shaped profile. This radius is then used by Blender to render the hair with a specific thickness.

**Key Properties & Settings:**

- **Geometry (Input):** The hair curve geometry to be affected.
    
- **Replace Radius (Input):** When enabled, this will completely overwrite any existing radius values on the curves.
    
- **Radius (Input):** The base radius or maximum thickness of the hair strands.
    
- **Shape (Input):** A float falloff (from 0 to 1) that multiplies the Radius along the length of each curve. This is the primary control for shaping the hair's profile.
    
- **Factor Min / Factor Max (Inputs):** These inputs remap the Shape falloff, allowing you to fine-tune the thinnest and thickest parts of the profile.
    

**Practical Application:**  
This node is the final and most essential step before rendering hair, as it controls the visible thickness of the strands. By default, hair curves have no thickness. This node is used to give them a natural, tapered shape.

- **The Goal:** To make procedurally generated animal fur look realistic by making each strand thick at the root and tapering to a fine point at the tip.
    
- **The Problem:** Raw hair curves are just infinitely thin lines. When rendered, they would be invisible or have a uniform, unnatural "spaghetti" look. Real hair is almost always thicker at its base and thinner at its end.
    
- - **The Solution:** Use the Set Hair Curve Profile node with a Curve Parameter to drive the shape.
        
    
    1. Place the Set Hair Curve Profile node at the very end of your node tree, just before the final Group Output.
        
    2. Set the Radius to the desired maximum thickness of the fur (e.g., a very small value like 0.001 meters).
        
    3. You need a way to control the Shape so it goes from 1.0 at the root to 0.0 at the tip. The Curve Parameter node (from the Input > Curve menu) provides exactly this: a value that smoothly transitions from 0 (root) to 1 (tip) along the curve's length.
        
    4. Because you want the root to be thick, you need to invert this. Use a Map Range node. Connect the Curve Parameter to the Value. Set From Min to 0 and From Max to 1. Set To Min to 1 and To Max to 0.
        
    5. Connect the result of this Map Range node into the Shape input.
        

The radius attribute is now set on every point of every curve. At the root, the radius will be 0.001 * 1.0, and at the tip, it will be 0.001 * 0.0, with a smooth linear transition in between. When rendered, this will produce a natural and believable tapered fur strand.