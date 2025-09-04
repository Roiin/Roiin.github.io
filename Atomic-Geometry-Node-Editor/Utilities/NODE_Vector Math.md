**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Vector)

**Core Function:** Performs a wide range of mathematical operations on input vectors, such as addition, subtraction, normalization, and distance calculation.

**Key Properties & Settings:**

- **Operation (Dropdown):** The core control that selects which mathematical function the node will perform. This changes the available input sockets and the type of output data. Key operations include:
    
    - **Add/Subtract/Multiply:** Perform element-wise arithmetic on two vectors.
        
    - **Length:** Calculates the magnitude (length) of a single input vector, outputting a scalar value.
        
    - **Distance:** Calculates the scalar distance between the two input vector positions.
        
    - **Normalize:** Outputs a vector with the same direction as the input but with a length of 1. This is essential for creating direction vectors.
        
    - **Cross Product:** Calculates a new vector that is perpendicular to the two input vectors.
        
    - **Scale:** Multiplies a vector by a single scalar value, uniformly scaling its length.
        
- **Inputs:** The sockets change based on the selected operation. The most common are two Vector inputs for binary operations, or a single Vector and a Scale float for the Scale operation.
    
- **Outputs:** The output is dynamic. Operations like Add or Normalize output a Vector, while operations like Length or Distance output a single floating-point Value.
    

**Practical Application:**  
The Vector Math node is a cornerstone of procedural modeling, especially for directing the orientation of instanced objects. Imagine creating a procedural animation of a swarm of particles, like flies or sparks, that must all turn to face a moving target.

- **The Goal:** To make every particle in a swarm individually orient itself to point towards a specific target object.
    
- **The Problem:** You cannot manually rotate thousands of particles. You need a procedural method that calculates the correct rotation for each particle based on its unique position relative to the target.
    
- **The Solution:** The key is to find the direction vector from each particle to the target. This is a classic use case for the Subtract operation.
    
    1. First, get the location of your target (e.g., using an Object Info node pointed at an Empty).
        
    2. Get the position of each individual particle using the Position field node.
        
    3. Feed these into a Vector Math node. Connect the **Target's Location** to the first Vector input and the particle's Position to the second.
        
    4. Set the Operation to **Subtract**. The formula Target Position - Particle Position results in a vector that points from the particle to the target.
        
    5. This output vector now represents the direction each particle should face. You can feed this direction into an Align Euler to Vector node to convert it into a rotation value, which can then be used to orient your instanced particles correctly. Every particle in the swarm will now realistically turn to face the target, no matter where it moves.