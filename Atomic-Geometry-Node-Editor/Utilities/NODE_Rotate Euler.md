**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation / Deprecated)

> **[!] DEPRECATION NOTICE**  
> This node is considered obsolete and has been replaced by the more modern **Rotate Rotation Node**. While it remains for backward compatibility, it is strongly recommended to use the new node in all current projects. The new node is more versatile, using the standard "Rotation" data socket.

**Core Function:** Applies a secondary rotation to an initial Euler rotation, with options for the rotation mode and coordinate space.

**Key Properties & Settings:**

- **Rotation Type (Property):** Switches the input mode between Euler (using a single vector) and Axis Angle (using a separate axis vector and angle float).
    
- **Space (Property):** Defines the coordinate system for the secondary rotation, typically Local for hierarchical rotations.
    
- **Rotation (Input):** The base Euler rotation.
    
- **Rotate By (Input):** The additional Euler rotation to apply (in Euler mode).
    
- **Rotation (Output):** The final, combined Euler rotation.
    

**Practical Application:**  
Historically, this node was fundamental for creating articulated hierarchies, such as the limbs of an animal. For example, to pose a spider leg, you would use this node to ensure the lower leg segment's rotation was relative to the upper leg segment's rotation.

- **The Goal:** To correctly pose a spider leg's lower segment (tibia) so that it hinges from the end of the already-rotated upper segment (femur).
    
- **The Problem:** The "knee bend" rotation must be applied in the femur's local coordinate space, not the world's.
    
- **The (Legacy) Solution:**
    
    1. Calculate the Femur_Rotation as an Euler vector.
        
    2. Create the Knee_Bend_Rotation as a separate Euler vector (e.g., using Combine XYZ to specify a rotation on a single axis).
        
    3. Use the Rotate Euler node. Set its Space property to Local.
        
    4. Connect the Femur_Rotation to the Rotation input and the Knee_Bend_Rotation to the Rotate By input.
        
    5. The output would be the final, correctly combined Euler rotation for the tibia.
        

This workflow is now handled more effectively by the **Rotate Rotation Node**, which should be used for all new projects.