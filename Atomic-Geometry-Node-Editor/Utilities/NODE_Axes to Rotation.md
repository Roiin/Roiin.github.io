**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Generates a stable rotation that aligns two of an object's local axes with two specified direction vectors.

**Key Properties & Settings:**

- **Primary Axis (Property):** The local axis (X, Y, or Z) that will be perfectly aligned with the Primary Axis input vector.
    
- **Secondary Axis (Property):** The local axis that will be aligned as closely as possible to the Secondary Axis input vector, after the primary alignment is satisfied.
    
- **Primary Axis (Input):** The target direction vector for the primary local axis. This is often a surface normal.
    
- **Secondary Axis (Input):** The target direction vector for the secondary local axis. This is often a surface tangent.
    
- **Rotation (Output):** The final Euler rotation that satisfies the alignment constraints.
    

**Practical Application:**  
This node is essential for controlling the "twist" or "roll" of an instanced object, which a simpler node like Align Rotation to Vector cannot do. Imagine you are procedurally placing leaves on a tree branch. You need the leaves to point outwards from the branch, but you also need their stems to align with the direction of the branch's growth.

- **The Goal:** To instance leaves on a branch so they point away from it and are also oriented along its length, without any random twisting.
    
- **The Problem:** Using Align Rotation to Vector with the branch's Normal will correctly make the leaves point outwards. However, the leaves can still spin freely around that normal vector. This can result in an unnatural, chaotic look where some leaves are sideways or upside down relative to the branch.
    
- **The Solution:** The Axes to Rotation node solves this by using a second vector to lock the twist.
    
    1. On the points where leaves will be instanced, you need two vectors: the Normal (pointing out from the branch) and the Tangent (pointing along the branch).
        
    2. Assume your leaf model's Z-axis is its "out" direction and its Y-axis is its "up" (stem) direction.
        
    3. Use the Axes to Rotation node.
        
        - Set the Primary Axis property to Z. Connect the branch's Normal vector to the Primary Axis input. This ensures the leaves point outwards.
            
        - Set the Secondary Axis property to Y. Connect the branch's Tangent vector to the Secondary Axis input. This will try to align the leaf's "up" direction with the direction of the branch.
            
    4. The Rotation output now provides a complete, stable orientation for each leaf.
        
    5. Feed this into the Rotation socket of your Instance on Points node.
        

The result is a natural-looking distribution where all the leaves are correctly oriented away from the branch and are also consistently aligned with its flow.