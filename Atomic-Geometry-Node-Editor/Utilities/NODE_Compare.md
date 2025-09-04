**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Compares two input values (A and B) based on a selected logical operation and outputs a Boolean result (True or False).

**Key Properties & Settings:**

- **Data Type:** The node can operate on various data types, including Float, Integer, Vector, and Color. The available modes and operations change with the data type.
    
- **Operation (Dropdown):** The comparison to perform, such as Greater Than, Less Than, Equal, or Not Equal.
    
- **Mode (Dropdown, Vector only):** Provides advanced comparison methods for vectors:
    
    - **Element-Wise:** Compares each component of the vectors individually.
        
    - **Length:** Compares the magnitude (length) of the two vectors.
        
    - **Direction:** Compares the angle between the two vectors against a threshold.
        
- **A / B (Inputs):** The two values to be compared.
    
- **Epsilon (Input):** A tolerance threshold for Equal and Not Equal operations, useful for handling floating-point inaccuracies.
    
- **Result (Output):** The Boolean outcome of the comparison.
    

**Practical Application:**  
This node is essential for creating selections based on geometric properties. The Direction mode is particularly powerful for isolating parts of a mesh based on their orientation. Imagine you are procedurally placing scales on a lizard model, and you want the scales to appear only on its back and the tops of its legs, not on its belly.

- **The Goal:** To create a Boolean mask that selects only the upward-facing surfaces of a lizard model.
    
- **The Problem:** Simply selecting surfaces based on their Z-height is unreliable for a complex, posed animal. You need a method that can identify which direction a surface is pointing, regardless of its absolute position.
    
- **The Solution:** Compare the direction of the mesh's Normal vector to the world's "up" direction.
    
    1. Use a Compare node set to the Vector data type.
        
    2. Change its Mode to Direction.
        
    3. Connect the mesh's Normal field into input A.
        
    4. For input B, use a Vector node with the value (0, 0, 1) to represent "straight up".
        
    5. Set the Operation to Less Than. The node now compares the angle between the surface normal and the up vector.
        
    6. Set the Angle input to a value like 1.57 (which is approximately PI/2, or 90 degrees).
        
    7. The Result will be True for every point on the mesh whose normal is pointing within 90 degrees of the world's Z-axis (i.e., the top surfaces). This Boolean field can be used directly as the Selection for an Instance on Points node to place your scales.