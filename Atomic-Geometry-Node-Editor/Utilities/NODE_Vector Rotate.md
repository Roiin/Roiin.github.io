**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Vector)

**Core Function:** Rotates an input vector around a specified pivot point and axis.

**Key Properties & Settings:**

- **Type (Dropdown):** Determines the method used to define the rotation.
    
    - **Axis Angle:** Rotates the input vector around an arbitrary Axis vector by a specific Angle. This is the most flexible method.
        
    - **X/Y/Z Axis:** A simpler mode that rotates the vector around one of the global axes (X, Y, or Z) by a given Angle.
        
    - **Euler:** Rotates the vector using X, Y, and Z rotation values provided by a separate Rotation vector input.
        
- **Vector (Input):** The vector that will be rotated.
    
- **Center (Input):** The pivot point around which the Vector will be rotated.
    
- **Axis (Input):** Defines the axis of rotation when the Type is set to 'Axis Angle'.
    
- **Angle (Input):** Defines the amount of rotation in radians.
    
- **Invert (Checkbox):** When checked, reverses the direction of the rotation.
    

**Practical Application:**  
This node is ideal for creating circular arrays of objects or procedural details. For example, consider modeling a procedural cart wheel with several spokes radiating from a central hub.

- **The Goal:** To arrange a number of "spoke" objects in a perfect circle, all pointing from the rim towards the center of a wheel.
    
- **The Problem:** You cannot simply instance the spokes; they would all appear at the same location with the same orientation. You need a method to calculate a unique, rotated position for each spoke around a central point.
    
- **The Solution:** The Vector Rotate node can generate these positions.
    
    1. Start with a single vector that represents the position of the first spoke, for instance, a vector of (1, 0, 0) for a wheel with a radius of 1 meter.
        
    2. On your instancer, for each instance (each spoke), you will calculate a unique rotation angle. A common formula is (2 * PI / number_of_spokes) * instance_index.
        
    3. Use a Vector Rotate node.
        
        - Set the Type to Z Axis to rotate around the wheel's axle.
            
        - Plug the single spoke position (1, 0, 0) into the Vector input.
            
        - Leave the Center at (0, 0, 0), the hub of the wheel.
            
        - Plug your calculated angle for each instance into the Angle input.
            
    4. The Vector output of this node will now provide a unique, perfectly rotated position for each spoke. When you use these vectors as the positions for your instanced spokes, they will form a perfect, evenly spaced wheel.