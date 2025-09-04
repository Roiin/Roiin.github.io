**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Field)

**Core Function:** Calculates the mean (average) and median of a field of values over a specified domain.

**Key Properties & Settings:**

- **Data Type (Property):** The type of data to be averaged. Can be set to Float or Vector.
    
- **Domain (Property):** The attribute domain (e.g., Points, Instances) over which the average is calculated.
    
- **Value (Input):** The field of values to be analyzed.
    
- **Group ID (Input):** An integer field used to partition the calculation. Elements with the same ID are grouped together, and an average is calculated for each group independently.
    
- **Mean (Output):** The average value for a given group (the sum of values divided by the element count).
    
- **Median (Output):** The middle value of the sorted set of values within a group.
    

**Practical Application:**  
This node is exceptionally useful for finding the geometric center of a collection of points. Imagine you have a procedural setup that generates a flock of birds or a swarm of particles, and you want to place a single "leader" object precisely in the middle of the entire group, no matter how the individual members move.

- **The Goal:** To find the center point of a dynamic particle swarm and place a separate object there.
    
- **The Problem:** A particle swarm is just a cloud of points. It doesn't have an intrinsic "center" or "origin" that you can easily reference. You need a way to calculate this central position based on the locations of all the individual particles.
    
- **The Solution:** The Field Average node, when set to Vector, calculates the average of position vectors, which is the geometric center of those points.
    
    1. Start with the geometry that contains your particle points.
        
    2. Use a Field Average node.
        
        - Set its Data Type to Vector.
            
        - Set its Domain to Point (or Instance if you are working with instances).
            
        - Connect the Position field into the Value input.
            
    3. The Mean output will now be a single vector that represents the exact center of the particle swarm.
        
    4. You can then use this vector to set the position of another object. For example, connect the Mean output to the Translation input of a Transform Geometry node that is affecting a sphere primitive.
        

This will place the sphere perfectly in the calculated center of the swarm. If the particles move, the average position is recalculated in real-time, and the "leader" sphere will move along with the swarm's center of mass.