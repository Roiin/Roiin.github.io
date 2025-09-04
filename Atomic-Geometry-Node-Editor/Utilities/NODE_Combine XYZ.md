**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Vector)

**Core Function:** Creates a single vector from three separate floating-point values for the X, Y, and Z components.

**Key Properties & Settings:**

- **X (Input):** A floating-point value that defines the X component of the output vector.
    
- **Y (Input):** A floating-point value that defines the Y component of the output vector.
    
- **Z (Input):** A floating-point value that defines the Z component of the output vector.
    
- **Vector (Output):** The resulting combined vector (X, Y, Z).
    

**Practical Application:**  
This node is essential when you need to control the individual components of a vector independently, such as for non-uniform scaling. Imagine you are creating a procedural model of a spider and you need to define the shape of its abdomen. You want separate controls for its length, width, and height.

- **The Goal:** To scale a primitive sphere into an oblong spider abdomen, with independent controls for its dimensions along the X, Y, and Z axes.
    
- **The Problem:** The Scale input on a Transform Geometry node accepts a single vector. You cannot directly plug in three separate values for "length," "width," and "height." Plugging a single value would scale the sphere uniformly, which is not what you want for an abdomen shape.
    
- **The Solution:** The Combine XYZ node acts as the perfect bridge.
    
    1. Start with a UV Sphere primitive to serve as the base for the abdomen.
        
    2. Add a Transform Geometry node to modify the sphere.
        
    3. Create three separate Value nodes (or inputs on your group) and name them "Length (X)", "Width (Y)", and "Height (Z)".
        
    4. Connect the "Length (X)" value to the X input of the Combine XYZ node.
        
    5. Connect "Width (Y)" to the Y input and "Height (Z)" to the Z input.
        
    6. Connect the final Vector output from the Combine XYZ node into the Scale socket of the Transform Geometry node.
        

Now, you can adjust the three value sliders independently to stretch and squash the sphere into the precise, non-uniform shape required for the spider's body, providing intuitive and direct control over the final model.