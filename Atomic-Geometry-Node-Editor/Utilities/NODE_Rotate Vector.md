**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Applies a standard rotation value to a vector, outputting its new direction or position after being rotated.

**Key Properties & Settings:**

- **Vector (Input):** The vector to be rotated. This can represent either a position in space or a direction.
    
- - **Rotation (Input):** The rotation to apply. This uses the standard rotation data socket, which is compatible with the outputs of other rotation nodes.
        
- **Vector (Output):** The final vector after the rotation has been applied.
    

**Practical Application:**  
This node is essential for transforming a local-space direction into a world-space direction. Imagine you are modeling a spider and you want to procedurally generate a silk strand shooting from its spinnerets. The direction the silk shoots is simple in the spider's own reference frame, but you need to find this direction in the world to create the effect.

- **The Goal:** To calculate the correct world-space velocity vector for a web strand being ejected from a spinneret on the spider's animated abdomen.
    
- **The Problem:** In the spider's local space, the direction of the web is a simple vector, like "straight back" (0, -1, 0). However, the spider's abdomen itself is rotated in the world. You need to apply this world rotation to the local direction to find the final, correct world-space vector for the silk.
    
- **The Solution:** The Rotate Vector node is the direct tool for this task.
    
    1. First, get the world Rotation of the spider's abdomen (e.g., calculated from an Align Rotation to Vector node or read from an Object Info node).
        
    2. Define the local direction of the silk strand using a Vector node (e.g., (0, -1, 0)).
        
    3. Use the Rotate Vector node.
        
        - Connect the local silk direction to the Vector input.
            
        - Connect the abdomen's world Rotation to the Rotation input.
            
    4. The Vector output is now the correct world-space direction. You can use this vector to set the velocity for a particle or as the extrusion direction for a curve, creating a web strand that shoots realistically from the spider's current orientation.