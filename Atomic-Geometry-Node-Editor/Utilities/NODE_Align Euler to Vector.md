**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation / Deprecated)

> **[!] DEPRECATION NOTICE**  
> This node is considered obsolete and has been replaced by the more modern **Align Rotation to Vector Node**. While it remains for backward compatibility with older files, it is strongly recommended to use the new node in all current projects. The functionality is identical, but the new node uses the standard "Rotation" data socket.

**Core Function:** Calculates the Euler rotation required to align a chosen local axis with a target direction vector.

**Key Properties & Settings:**

- **Axis (Property):** The local axis of the object (X, Y, or Z) that you want to point towards the target vector.
    
- **Rotation (Input):** An optional initial Euler rotation to be applied before the alignment.
    
- **Factor (Input):** Controls the strength of the alignment, where 1.0 is a perfect alignment.
    
- **Vector (Input):** The target direction vector that the chosen axis will be aligned to.
    
- **Rotation (Output):** The final calculated Euler rotation.
    

**Practical Application:**  
Historically, this was the primary node used for orienting instances. For example, to make a procedural school of fish point in the direction they are swimming, you would use this node to convert their velocity vectors into a usable rotation.

- **The Goal:** To orient instanced fish to face their direction of travel.
    
- **The Problem:** A velocity vector is a direction, not a rotation. It must be converted into Euler angles to orient an object.
    
- **The (Legacy) Solution:**
    
    1. Assuming the fish model is oriented along its local Y-axis, you would set the Axis property of this node to Y.
        
    2. The Velocity vector for each fish would be connected to the Vector input.
        
    3. The Rotation output would then be connected to the Rotation socket of an Instance on Points node.
        

This workflow is now handled by the **Align Rotation to Vector Node**, which should be used for all new projects.