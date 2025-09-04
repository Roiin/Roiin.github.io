**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Vector)

**Core Function:** Splits a single input vector into its three individual floating-point components: X, Y, and Z.

**Key Properties & Settings:**

- **Vector (Input):** The source vector to be deconstructed.
    
- **X (Output):** A floating-point value representing the X component of the input vector.
    
- **Y (Output):** A floating-point value representing the Y component of the input vector.
    
- **Z (Output):** A floating-point value representing the Z component of the input vector.
    

**Practical Application:**  
This node is crucial when you need to use a single dimension from a vector to control another attribute. For instance, imagine you are populating a procedural tree with leaves and you want the leaves at the top to be larger than the leaves at the bottom, simulating how they might grow to catch more sunlight.

- **The Goal:** To control the scale of instanced leaves based only on their height (Z-axis position) on the tree.
    
- **The Problem:** The Position of each leaf is a vector (X, Y, Z). The Scale input on the Instance on Points node, however, needs a single float value for uniform scaling. You cannot directly plug the position vector into the scale socket; you must first isolate the Z-component.
    
- **The Solution:** The Separate XYZ node is designed for exactly this task.
    
    1. After you have the points on your tree where leaves will be instanced, get their Position field.
        
    2. Connect this Position vector to the Vector input of the Separate XYZ node.
        
    3. Take the Z output. This value now represents the absolute height of each leaf point.
        
    4. You can use this Z value directly, or for more control, pass it through a Map Range node to fine-tune the relationship between height and scale (e.g., mapping the tree's total height from 0m-10m to a scale range of 0.5-1.0).
        
    5. Connect the final value into the Scale input of your Instance on Points node.
        

The result is a procedural effect where leaves automatically become larger the higher they are on the tree, adding a significant layer of realism with a simple and logical node setup.