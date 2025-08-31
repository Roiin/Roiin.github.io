- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Properties
    
- **Core Function:** Performs a direct mathematical operation on a numerical Game Property of an object, modifying its existing value.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Operation (Dropdown):** In your screenshot, this is labeled Add. Other likely options are Subtract, Multiply, Divide, Assign.
        
    - **Object (Socket):** The target object whose property will be modified.
        
    - **Game Property (Socket):** String input for the name of the property.
        
    - **Value (Socket):** The numerical value to be used in the operation (e.g., the amount to add or subtract).
        
    - **Clamp (Checkbox):** Prevents the property's value from going above or below a specified range (Min/Max inputs appear when checked).
        
- **Practical Application:** A highly efficient way to handle common value changes. Instead of using Get Property, Math, and Set Property, this single node can be used to "Add 10" to a score or "Subtract 25" from health. The Clamp feature is excellent for preventing health from going below 0.