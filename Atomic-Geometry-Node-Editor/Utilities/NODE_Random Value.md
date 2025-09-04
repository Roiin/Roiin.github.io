**Editor:** Geometry Nodes Editor  
**Node Group:** Control (Random)

**Core Function:** Generates a field of pseudo-random numbers, vectors, or booleans, which is essential for adding natural variation to procedural effects.

**Key Properties & Settings:**

- **Data Type (Property):** Determines the kind of random value to generate.
    
    - **Float:** A decimal number within a range.
        
    - **Integer:** A whole number within a range.
        
    - **Vector:** A 3D vector where each component is randomized within a range.
        
    - **Boolean:** An on/off value (True or False) based on a set probability.
        
- **Min / Max (Inputs):** Define the lower and upper bounds for the random Float, Integer, or Vector outputs.
    
- **Probability (Input):** A value from 0.0 to 1.0 that sets the chance of the Boolean output being True.
    
- **ID (Input):** An integer field used as the "question" for the random number generator. By default, this is the element's index, ensuring each point, face, or instance gets its own unique random value. Providing a constant ID results in a single random value for all elements.
    
- **Seed (Input):** An additional integer that alters the random sequence. Changing the seed will generate a different set of random values for the same set of IDs.
    
- **Value (Output):** The final field of generated random values.
    

**Practical Application:**  
This node is the cornerstone of creating organic, non-uniform results. Its most common use is to add variation to instanced objects. Imagine you are creating a procedural forest by scattering tree models on a plane.

- **The Goal:** To transform a uniform grid of identical trees into a natural-looking forest where each tree has a random height and a random rotation.
    
- **The Problem:** Simply instancing a tree on a grid of points results in a sterile, artificial-looking plantation. Every tree is the same size and faces the same direction.
    
- **The Solution:** Use two Random Value nodes to drive the Scale and Rotation of the instances.
    
    1. **For Random Scale:**
        
        - Use a Random Value node set to Float.
            
        - Set the Min to 0.8 (for a smallest tree of 80% size) and the Max to 1.5 (for a largest tree of 150% size).
            
        - Connect its Value output directly into the Scale socket of your Instance on Points node.
            
    2. **For Random Rotation:**
        
        - Use a second Random Value node, also set to Float.
            
        - Set the Min to 0.0 and the Max to 6.283 (which is 2 * PI, or a full 360-degree circle in radians).
            
        - Use a Combine XYZ node. Connect the random float Value into the Z input, leaving X and Y at 0. This creates a rotation vector that only affects the vertical axis.
            
        - Connect this vector to the Rotation socket of the Instance on Points node.
            

The result is a forest that looks far more natural. Each tree is now a unique height and is twisted to a random heading, breaking up the uniformity and creating a believable, organic scene.