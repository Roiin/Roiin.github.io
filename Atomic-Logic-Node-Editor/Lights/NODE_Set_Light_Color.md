- **Editor:** Logic Node Editor
    
- **Node Group:** Lights
    
- **Core Function:** Sets the color of a specified Light object.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control output that pulses after the operation is complete.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Light Object (Socket):** The target Light object to modify.
        
    - **Color (Socket):** A 3D vector input for the new RGB color. This can be connected to a Color RGB node for easy selection.
        
- **Practical Application:** Essential for dynamic lighting effects. Examples: making a light flash red for an alarm, changing the color of a magical crystal as it powers up, or simulating a day/night cycle by shifting the sun lamp's color from a warm yellow to a cool blue.