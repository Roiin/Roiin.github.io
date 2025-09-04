**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Deconstructs a standard rotation value into its four individual quaternion components (W, X, Y, and Z).

**Key Properties & Settings:**

- **Rotation (Input):** The standard rotation value to be converted.
    
- **W, X, Y, Z (Outputs):** Four separate float values that represent the components of the quaternion.
    

**Practical Application:**  
This node, used in conjunction with its counterpart Quaternion to Rotation, provides access to a more robust method of interpolating between two rotations. Quaternions avoid the "gimbal lock" issue that can cause strange spinning artifacts when mixing standard Euler angles. Imagine you are animating a spider crawling from a vertical wall onto the ceiling.

- **The Goal:** To create a smooth and natural rotational transition for the spider as it moves from its wall-aligned orientation to its ceiling-aligned orientation.
    
- **The Problem:** If you try to mix the two Euler rotations directly (e.g., using a Mix Vector node on their Euler representations), the spider might spin unexpectedly during the transition. This is a common issue with Euler angle interpolation.
    
- **The Solution:** Performing the interpolation in quaternion space provides a much more stable result. The Rotation to Quaternion node is the first step in this process.
    
    1. First, determine the spider's starting rotation on the wall (Rotation_A) and its ending rotation on the ceiling (Rotation_B).
        
    2. Use two Rotation to Quaternion nodes, one for Rotation_A and one for Rotation_B. This will give you two sets of W, X, Y, Z components.
        
    3. Use four separate Mix (Float) nodes. Connect the W components from both quaternions to the first mix node, the X components to the second, and so on for Y and Z.
        
    4. Drive the Factor of all four mix nodes with a single slider (e.g., a 0-1 value representing the progress of the transition).
        
    5. Feed the four mixed W, X, Y, and Z outputs into a Quaternion to Rotation node.
        
    6. The result is a single, smoothly interpolated rotation that you can apply to your spider model, ensuring it turns predictably and naturally as it crawls onto the ceiling.