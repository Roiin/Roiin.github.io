- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 2 - Bricks
    
- **Core Function:** Modifies a value within a specific field of a legacy Logic Brick Actuator, allowing nodes to control actuator parameters.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The object that owns the actuator.
        
    - **Input (Actuator):** The name of the Actuator to modify.
        
    - **Input (Attribute):** The name of the field/attribute to change.
        
    - **Input (Float):** The new value to assign to the attribute.
        
    - **Output (Done):** A flow control pulse that activates after the value is set.
        
- **Practical Application:** Dynamically changing the strength of a Motion actuator for variable movement speed, or swapping the animation being played by an Action actuator.