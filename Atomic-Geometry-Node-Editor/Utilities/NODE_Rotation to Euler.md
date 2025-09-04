**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Deconstructs a standard rotation data type into its component Euler angles (X, Y, and Z).

**Key Properties & Settings:**

- **Rotation (Input):** The standard rotation value to be deconstructed.
    
- **Euler (Output):** A vector where the X, Y, and Z components represent the angles of rotation around each axis in radians.
    

**Practical Application:**  
This node is essential when you need to isolate and use a single axis of rotation from a complex orientation. Imagine you have a procedurally animated spider walking over uneven terrain. Its body has a complex rotation to align with the ground, but you want its head to perform a separate "looking around" animation based only on the body's yaw (side-to-side rotation).

- **The Goal:** To make a spider's head turn left and right based on its body's yaw, while ignoring the body's pitch (up/down tilt) and roll.
    
- **The Problem:** The spider's body orientation is a single, complex Rotation value that combines pitch, roll, and yaw. You cannot directly use this to rotate the head, as the head would tilt and roll undesirably along with the body. You need to extract just the Z-axis rotation (yaw).
    
- **The Solution:** The Rotation to Euler node breaks the combined rotation into its individual components.
    
    1. Take the final Rotation value that orients the spider's body.
        
    2. Connect this to the Rotation input of the Rotation to Euler node.
        
    3. The Euler output is a vector containing the three angles. Use a Separate XYZ node to access them. The Z output float is the yaw value you need.
        
    4. You can now use this single Z-axis angle to drive the head's rotation. Use a Combine XYZ node, plugging the Z value into the Z socket, and then use the resulting vector to transform the head geometry.
        

This allows you to create a secondary animation layer for the head that is procedurally linked to the body's primary orientation but isolated to a single, controlled axis of movement.