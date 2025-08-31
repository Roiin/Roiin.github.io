- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Applies a continuous rotational force to an object, causing it to turn or spin smoothly.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Local (Checkbox):** If checked, the Rotation vector applies rotation around the object's local axes. If unchecked, it uses world axes.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The target object to rotate.
        
    - **Vector (Socket):** A 3D vector where each component (X, Y, Z) represents the speed of rotation around that axis.
        
- **Practical Application:** Used for smooth turning controls. For example, a keyboard input can provide a vector of (0, 0, 5.0) to make a character turn at a constant speed. Also used for continuously spinning objects like fans or propellers.