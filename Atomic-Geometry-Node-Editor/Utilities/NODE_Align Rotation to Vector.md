**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Calculates the rotation required to align a chosen local axis with a target direction vector.

**Key Properties & Settings:**

- **Axis (Property):** The local axis of the object that you want to point towards the target vector (e.g., setting this to Y means "point the Y-axis").
    
- **Pivot (Property):** The axis around which the rotation will occur. Auto is often the best choice as it calculates the most direct rotation.
    
- **Rotation (Input):** An optional initial rotation to be applied before the alignment.
    
- **Factor (Input):** Controls the strength of the alignment. A factor of 1.0 results in a perfect alignment, while 0.0 results in no change.
    
- **Vector (Input):** The target direction vector that the chosen Axis will be aligned to.
    
- **Rotation (Output):** The final calculated Euler rotation.
    

**Practical Application:**  
This node is the primary tool for orienting instanced objects to face a specific direction. A classic use case is creating a school of fish where each fish must point in the direction it is swimming.

- **The Goal:** To make each fish in a procedurally animated school orient itself to face its individual velocity vector.
    
- **The Problem:** You can calculate a velocity vector for each fish (e.g., using a Noise Texture to create a flow field), but this is just a direction in space. You cannot directly plug this direction vector into an Instance on Points node's Rotation socket; you must first convert it into a usable Euler rotation.
    
- **The Solution:** The Align Rotation to Vector node performs this exact conversion.
    
    1. Assume your base fish model is modeled pointing along its own local Y-axis.
        
    2. After generating the points for your school, calculate the Velocity vector for each point.
        
    3. Use an Align Rotation to Vector node.
        
        - Set the Axis property to Y, to match the orientation of your fish model.
            
        - Plug the Velocity vector field into the Vector input.
            
        - Leave the Factor at 1.0 for perfect alignment.
            
    4. The Rotation output of this node is now the correct Euler rotation for each individual fish.
        
    5. Connect this Rotation output to the Rotation input of your Instance on Points node.
        

The result is a dynamic school of fish where every individual realistically turns and orients itself along its path of motion, creating a believable and lifelike animation.