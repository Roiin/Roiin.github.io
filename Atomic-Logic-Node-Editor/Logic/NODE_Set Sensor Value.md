- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 2 - Bricks
    
- **Core Function:** Modifies a value within a specific field of a legacy Logic Brick Sensor, allowing nodes to configure sensors dynamically at runtime.
    
- - **Key Properties & Settings:**
        
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Object):** The object that owns the sensor.
        
    - **Input (Sensor):** The name of the Sensor to modify.
        
    - **Input (Attribute):** The name of the field/attribute to change.
        
    - **Input (Float):** The new value to assign to the attribute.
        
    - **Output (Done):** A flow control pulse that activates after the value is set.
        
- **Practical Application:** Programmatically changing the property a Property sensor is looking for, or altering the range of a Near sensor based on game events.