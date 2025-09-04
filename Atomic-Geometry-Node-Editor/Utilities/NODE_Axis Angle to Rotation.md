**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Creates a standard Euler rotation from an axis-angle representation (an axis vector and an angle of rotation around that axis).

**Key Properties & Settings:**

- **Axis (Input):** A vector that defines the axis around which the rotation will occur. This vector is usually normalized.
    
- **Angle (Input):** A float value, in radians, specifying the amount of rotation around the given axis.
    
- **Rotation (Output):** The resulting Euler rotation value.
    

**Practical Application:**  
This node is essential for creating rotations that are not aligned with the global X, Y, or Z axes. A perfect example is arranging the legs of a spider radially around its body, especially when the body is tilted on an uneven surface.

- **The Goal:** To arrange eight spider legs in a perfect circle, radiating outwards from the spider's tilted cephalothorax (main body section).
    
- **The Problem:** If you simply rotate the legs around the world's Z-axis (0,0,1), they will be arranged in a flat, horizontal circle. If the spider's body is tilted, this will look incorrect, with some legs pointing up into the air and others clipping into the ground. The legs must rotate around the body's own "up" axis.
    
- **The Solution:** The Axis Angle to Rotation node allows you to use the body's surface normal as the custom rotation axis.
    
    1. First, find the normal vector of the spider's body at the central point where the legs connect. This vector represents the local "up" direction for the body.
        
    2. For each leg instance (from index 0 to 7), you need to calculate its angle in the circle. The formula is (2 * PI / 8) * Instance Index.
        
    3. Use the Axis Angle to Rotation node.
        
        - Connect the body's Normal vector into the Axis input.
            
        - Connect the calculated angle for each instance into the Angle input.
            
    4. The Rotation output is now the correct orientation for each leg.
        
    5. When you use this output in the Rotation socket of your Instance on Points node, each leg will be perfectly rotated around the spider's tilted body, ensuring they all splay outwards correctly relative to the surface it is standing on.