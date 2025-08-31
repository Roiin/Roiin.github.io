
**Editor:** Logic Node Editor
    
  **Node Group:** Objects Part 4 - Object Data
    
- **Core Function:** Modifies a specific numerical attribute of a physics constraint.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The object that possesses the physics constraint.
        
    - **Input (Constraint):** The name of the constraint to be modified (as a string).
        
    - **Input (Attribute):** The name of the attribute within the constraint to change (e.g., "min_angle").
        
    - **Input (Value):** The new numerical value for the attribute.
        
    - **Output (Done):** A flow control pulse that activates after the attribute is set.
        
- **Practical Application:** Dynamically changing the properties of a hinge or a spring in-game. For example, making a rope bridge more "bouncy" by changing its springiness attribute when a heavy character walks on it.