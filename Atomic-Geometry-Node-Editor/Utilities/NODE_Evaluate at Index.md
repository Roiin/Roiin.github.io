**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Field)

**Core Function:** Retrieves the value of a field from a specific element at a given index within a chosen domain.

**Key Properties & Settings:**

- **Domain (Property):** The attribute domain from which to retrieve the data (e.g., Point, Edge, Face, Spline). This can be different from the domain the node is currently being evaluated on.
    
- **Index (Input):** An integer specifying the exact element to sample from. For example, an index of 0 would sample the very first element in the specified domain.
    
- **Value (Input):** The field data to be read. For example, connecting the Position field will allow you to read the position of the indexed element.
    
- **Value (Output):** The data value of the field at the specified index.
    

**Practical Application:**  
This node is useful when you need to make the behavior of many elements dependent on a single, specific element. Imagine creating a procedural animation where a swarm of particles (like bees or small animals) must all point towards the leader of the swarm, which is always the very first particle (index 0).

- **The Goal:** To orient all particles in a set to face the particle at index 0.
    
- **The Problem:** To orient an object, you need a direction vector. For any given particle, this direction vector is (Position of Leader) - (Position of self). The challenge is getting the "Position of Leader" and making it available to every other particle in the swarm.
    
- **The Solution:** The Evaluate at Index node can retrieve the leader's position and broadcast it to all other particles.
    
    1. Start with your set of points (the particle swarm).
        
    2. Use an Align Euler to Vector node to control the rotation of instances on those points.
        
    3. To calculate the direction vector, you need the leader's position. Use an Evaluate at Index node.
        
        - Set the Domain to Points.
            
        - Set the Index to 0.
            
        - Connect the Position field into the Value input.
            
    4. The output of this node will now be the position vector of the first particle, and this same value is available to every other point in the context.
        
    5. Use a Vector Math (Subtract) node. Subtract the current particle's Position from the leader's position (the output of the Evaluate at Index node).
        
    6. The result is the required direction vector. Feed this into the Vector input of the Align Euler to Vector node.
        

Now, every instanced object in your particle swarm will correctly orient itself to face the leader particle, regardless of where the particles move.