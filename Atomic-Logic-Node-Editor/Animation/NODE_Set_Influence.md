- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Bone Constraints
    
- **Core Function:** A specialized and more user-friendly version of Set Attribute that directly targets the "Influence" property of a Bone Constraint. This controls how strongly the constraint affects the bone, from 0.0 (no effect) to 1.0 (full effect).
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input.
        
    - **Armature (Socket):** The armature object.
        
    - **Bone Name (Selector):** A dropdown to select the bone.
        
    - **Constraint Name (Selector):** A dropdown to select the constraint.
        
    - **Influence (Socket):** A float input (clamped 0.0 to 1.0) for the new influence value.
        
- **Practical Application:** Essential for blending constraints on and off. For instance, a character could have a "Copy Rotation" constraint to make their head track a target. You can smoothly increase the Influence from 0.0 to 1.0 when the player aims, and then decrease it back to 0.0 when they stop, allowing the head to return to its normal animation.