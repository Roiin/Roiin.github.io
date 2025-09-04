**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Reconstructs a standard rotation value from its four individual quaternion components (W, X, Y, and Z).

**Key Properties & Settings:**

- **W, X, Y, Z (Inputs):** Four separate float values that represent the components of the quaternion.
    
- **Rotation (Output):** The final, combined standard rotation value.
    

**Practical Application:**  
This node is the essential counterpart to the Rotation to Quaternion node and is the final step in performing a stable, gimbal-lock-free interpolation between two rotations. Continuing the example of animating a spider crawling from a vertical wall to the ceiling:

- **The Goal:** To apply the smoothly blended quaternion values to the spider model to complete its transition from the wall to the ceiling.
    
- **The Problem:** In the previous step (using the Rotation to Quaternion node), you deconstructed the start and end rotations and used Mix (Float) nodes to blend their individual W, X, Y, and Z components. You now have four separate mixed float values, but you need a single, usable Rotation output to orient the spider.
    
- **The Solution:** The Quaternion to Rotation node reassembles these components into the final rotation.
    
    1. Take the four Result outputs from your Mix (Float) nodes—one for each component (W, X, Y, Z).
        
    2. Connect the mixed W value to the W input of the Quaternion to Rotation node.
        
    3. Connect the mixed X, Y, and Z values to their corresponding X, Y, and Z inputs.
        
    4. The Rotation output of this node is now the final, smoothly interpolated orientation for the spider.
        
    5. Feed this single Rotation output into the Rotation socket of the Transform Geometry or Instance on Points node affecting your spider model.
        

By using this quaternion-based workflow, the spider will now perform a clean, predictable turn as it moves from the wall to the ceiling, completely avoiding the erratic spinning that can occur when attempting to mix Euler angles directly.