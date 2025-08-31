- **Editor:** Logic Node Editor
    
- **Node Group:** Lights
    
- **Core Function:** Sets the power (intensity/energy) of a specified Light object.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control output.
        
    - **Condition (Socket):** A boolean input.
        
    - **Light Object (Socket):** The target Light object.
        
    - **Power (Socket):** A float input for the new power value.
        
- **Practical Application:** Fundamental for dynamic brightness effects. Used to make lights flicker, fade in or out, or pulse. For example, a Sine wave from a Math node could be used to drive the Power input to create a pulsing magical glow.