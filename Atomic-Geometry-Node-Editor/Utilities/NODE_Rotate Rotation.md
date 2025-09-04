**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Combines two rotations by applying a second rotation on top of an initial rotation, with the option to perform the operation in either local or global space.

**Key Properties & Settings:**

- **Space (Property):** Determines the coordinate system for the second rotation.
    
    - **Local:** The Rotate By value is applied relative to the axes defined by the initial Rotation input.
        
    - **Global:** The Rotate By value is applied using the world's X, Y, and Z axes.
        
- **Rotation (Input):** The base or starting rotation.
    
- **Rotate By (Input):** The additional rotation to apply.
    
- **Rotation (Output):** The final, combined rotation.
    

**Practical Application:**  
This node is fundamental for creating articulated hierarchies, such as the limbs of an animal, where the orientation of one part depends on the orientation of the part before it. A perfect example is posing a multi-segmented spider leg.

- **The Goal:** To correctly pose a spider leg's lower segment (tibia) so that it hinges correctly from the end of the already-rotated upper segment (femur).
    
- **The Problem:** You have a rotation for the femur, positioning it relative to the spider's body. You also have a separate rotation representing the "knee bend" for the tibia. If you simply apply the knee bend rotation, it will be in world space, not relative to the femur, causing the leg to break apart visually.
    
- **The Solution:** The Rotate Rotation node in Local space solves this by creating a parent-child relationship between the rotations.
    
    1. First, calculate the Femur_Rotation (the orientation of the upper leg segment).
        
    2. Next, create the Knee_Bend_Rotation. This would be a simple rotation around a single axis (e.g., 45 degrees on the local X-axis) to create the joint bend.
        
    3. Use a Rotate Rotation node.
        
        - Set the Space to Local. This is the critical step.
            
        - Connect the Femur_Rotation to the Rotation input.
            
        - Connect the Knee_Bend_Rotation to the Rotate By input.
            
    4. The Rotation output is now the correct final orientation for the tibia. It has inherited the femur's rotation first, and then the knee bend has been applied relative to the femur's new orientation. You can feed this output into the Rotation socket for the tibia instance.
        

This correctly chains the rotations, allowing you to build complex, articulated limbs that pose realistically.