- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Bone Constraints
    
- **Core Function:** Sets or changes the target object for a Bone Constraint at runtime.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input.
        
    - **Armature (Socket):** The armature object.
        
    - **Bone Name (Selector):** A dropdown to select the bone.
        
    - **Constraint Name (Selector):** A dropdown to select the constraint (e.g., an IK or Damped Track constraint).
        
    - **Target (Socket):** An object input that specifies the new target for the constraint.
        
- **Practical Application:** Used for dynamic targeting systems. A character's head tracking constraint can be retargeted from one enemy to another. An IK constraint for a hand can be retargeted from its default position to a doorknob object when the player wishes to open a door.