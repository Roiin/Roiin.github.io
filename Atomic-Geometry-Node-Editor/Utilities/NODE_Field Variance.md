**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Field)

**Core Function:** Computes the variance and standard deviation of a field, measuring how much the values spread out from their average.

**Key Properties & Settings:**

- **Data Type (Property):** Sets the type of data to be analyzed, either Float or Vector.
    
- **Domain (Property):** The attribute domain (e.g., Points, Instances) over which the variance is calculated.
    
- **Value (Input):** The field of values to be measured.
    
- **Group ID (Input):** An integer field used to perform separate variance calculations for different groups of elements.
    
- **Variance (Output):** A measure of the average squared distance of each value from the mean. A higher value indicates a wider spread.
    
- **Standard Deviation (Output):** The square root of the variance, providing a more intuitive measure of the data's spread.
    

**Practical Application:**  
This node can be used to analyze the shape of geometry and make procedural decisions. For example, imagine you are generating a procedural forest and want to automatically apply a different material to trees that are straight versus trees that are gnarled and crooked.

- **The Goal:** To procedurally distinguish between straight and crooked trees in a collection of instanced tree models.
    
- **The Problem:** "Crookedness" is a visual concept. To make a decision in Geometry Nodes, you need to translate it into a single numerical value. A tree's "crookedness" can be defined by how much its vertices deviate from a central axis.
    
- **The Solution:** The Field Variance node can measure this deviation.
    
    1. Assume you have multiple tree objects instanced. The Instance Index can be used as the Group ID to analyze each tree individually.
        
    2. Feed the Position field of the tree geometry into the Value input of the Field Variance node.
        
    3. For a perfectly straight tree growing up the Z-axis, the positions of its vertices will have a very low variance on the X and Y axes. A crooked, gnarled tree will have a high variance in X and Y.
        
    4. The Variance output will be a vector. You can separate it (Separate XYZ) and add the X and Y components to get a single "crookedness" score for each tree instance.
        
    5. This score can then be used to drive a Material Selection or Set Material Index node. For example, if the crookedness score is above a certain threshold, assign a mossy, old-growth material; otherwise, assign a standard, healthy bark material.
        

This allows the system to automatically categorize and texture assets based on a quantifiable analysis of their shape.