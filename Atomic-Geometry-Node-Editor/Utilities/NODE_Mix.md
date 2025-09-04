**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Blends between two floating-point values (A and B) using a Factor to control the interpolation between them.

**Key Properties & Settings:**

- **Data Type (Property):** Set to Float for this context.
    
- **Factor (Input):** A float value that controls the blend. A factor of 0.0 outputs A, 1.0 outputs B, and 0.5 outputs an even mixture.
    
- **A (Input):** The first float value.
    
- **B (Input):** The second float value.
    
- **Clamp Factor (Checkbox):** When checked, it constrains the Factor input to the 0.0 to 1.0 range. Disabling this allows for extrapolation.
    
- **Result (Output):** The final blended float value.
    

**Practical Application:**  
This node is fundamental for creating smooth, controllable transitions between two different states of any attribute. For example, imagine you are procedurally creating a window with adjustable louvers (blinds) and you want a single slider to control the angle of all the louvers from fully open to fully closed.

- **The Goal:** To create a single "Louver Angle" slider (0.0 to 1.0) that smoothly rotates a set of instanced louvers from a horizontal (open) position to a vertical (closed) position.
    
- **The Problem:** The "open" state corresponds to a rotation of 0 degrees, while the "closed" state is 90 degrees (or PI/2 radians). You need a way to translate a simple 0-1 slider value into this specific angle range. While a Map Range node could work, the Mix node is often more direct for blending between two known endpoint values.
    
- **The Solution:** Use the Mix node to interpolate between the open and closed angles.
    
    1. On the points where your louvers are instanced, you need to set their rotation.
        
    2. Use a Mix node.
        
        - Set value A to 0.0 (representing 0 degrees, the fully open state).
            
        - Set value B to 1.5708 (representing PI/2 radians or 90 degrees, the fully closed state).
            
    3. Create a group input for your node setup, a float slider named "Louver Angle" with a range from 0.0 to 1.0.
        
    4. Connect this "Louver Angle" slider to the Factor input of the Mix node.
        
    5. The Result of the Mix node is the calculated angle in radians. Use a Combine XYZ node to apply this angle to the appropriate rotation axis (e.g., the X-axis).
        
    6. Feed this final rotation vector into the Rotation socket of your Instance on Points node.
        

Now, as you drag the "Louver Angle" slider from 0.0 to 1.0, all the instanced louvers will rotate smoothly and in unison from their open state to their closed state.