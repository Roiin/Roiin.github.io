**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Vector)

**Core Function:** Remaps the individual X, Y, and Z components of an input vector using a graphical curve widget for each channel.

**Key Properties & Settings:**

- **Vector (Input):** The source vector to be remapped. This is often a mesh's Position field.
    
- **Curve Widget:** The primary interface for defining the remapping transformation. By adding and manipulating points on the graph, you create a curve that dictates the output value for any given input value.
    
- **X, Y, Z (Buttons):** These tabs switch the curve widget to edit the remapping curve for the corresponding component of the input vector.
    
- **Vector (Output):** The final vector calculated after each of its components has been passed through its respective user-defined curve.
    

**Practical Application:**  
This node is excellent for creating complex, non-linear deformations of geometry. Imagine you are procedurally modeling a stylized tree for an animation. You want the trunk to have a gentle, organic bend, rather than being a perfectly straight cylinder.

- **The Goal:** To deform a straight vertical cylinder into a smoothly curved tree trunk.
    
- **The Problem:** A simple Transform node can only move, rotate, or scale the entire object uniformly. It cannot introduce a curve or bend along the object's length.
    
- **The Solution:** The Vector Curves node can remap the cylinder's vertex positions.
    
    1. Start with a Cylinder mesh primitive node.
        
    2. Use a Set Position node to modify its geometry.
        
    3. Connect the Position field into the Vector input of the Vector Curves node.
        
    4. In the Vector Curves node, select the **X** channel's curve. Leave the Y and Z channels as the default straight diagonal line.
        
    5. Add a point to the middle of the X curve and drag it upwards. This tells Blender: "For vertices in the middle of the cylinder's height, push their X-position further out. For vertices at the top and bottom, leave their X-position alone."
        
    6. Connect the Vector output of the Vector Curves node into the Position input of the Set Position node.
        

The result is that the straight cylinder is now smoothly bent along its X-axis, following the precise curve you drew. This creates a much more natural and visually appealing tree trunk than a simple, rigid cylinder.