- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Bone Constraints
    
- **Core Function:** Sets the value of a specific attribute (property) on a Bone Constraint.
    
- **System Note:** The name "Set Attribute" is generic. Its actual function is context-dependent based on the selected Attribute. This node acts as a universal modifier for various constraint properties.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A Boolean input; the node only executes if this is True.
        
    - **Armature (Socket):** The armature object that owns the bone with the constraint.
        
    - **Bone Name (Selector):** A dropdown to select the specific bone that has the constraint.
        
    - **Constraint Name (Selector):** A dropdown to select the target constraint on that bone (e.g., "IK", "Copy Rotation").
        
    - **Attribute (Socket):** A string input for the name of the constraint's property to modify (e.g., "influence").
        
    - **Float (Socket):** A float input for the new value of the attribute.
        
- **Practical Application:** A powerful node for fine-tuning constraints at runtime. For example, you could dynamically change the "Head/Tail" property of an IK constraint to make a character's foot point towards or away from its target.