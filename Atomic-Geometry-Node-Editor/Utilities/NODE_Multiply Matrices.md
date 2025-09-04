**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Combines two transformation matrices into a single matrix that represents the sequential application of both transformations.

**Key Properties & Settings:**

- **Matrix (Input):** The first transformation matrix.
    
- **Matrix (Input):** The second transformation matrix. The order matters; this transformation is applied relative to the first.
    
- **Matrix (Output):** The single resulting transformation matrix.
    

**Practical Application:**  
This node is essential for creating hierarchical chains of motion, where the movement of one object is relative to the movement of another. This is the core principle behind creating articulated limbs for a procedural animal, like a spider leg.

- **The Goal:** To correctly pose a multi-segmented spider leg so that when the upper segment rotates, the lower segments follow it naturally.
    
- **The Problem:** A spider leg has multiple joints (e.g., femur, tibia). If you create a transformation for the femur (e.g., rotating it away from the body) and a separate transformation for the tibia (e.g., bending the knee joint), applying them individually will not work. The tibia's transformation needs to happen after and relative to the femur's new position.
    
- **The Solution:** Multiply Matrices chains these relative transformations together.
    
    1. Create a transformation matrix for the femur segment. Let's call this Femur_Transform. This matrix positions and rotates the femur relative to the spider's body.
        
    2. Create a local transformation matrix for the tibia. This matrix describes how the tibia should bend relative to the end of the femur. Let's call this Tibia_Local_Transform.
        
    3. Use a Multiply Matrices node. Connect Femur_Transform to the first input and Tibia_Local_Transform to the second.
        
    4. The Matrix output now represents the final, combined transformation for the tibia. When you apply this matrix to the tibia geometry, it will first be moved into place by the femur's transformation, and then the local knee-bend rotation will be applied.
        

This creates a parent-child relationship between the transformations, allowing you to build complex, articulated limbs that move realistically.