**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Field)

**Core Function:** Calculates a running total of a set of values, outputting the intermediate sum at each element.

**Key Properties & Settings:**

- **Data Type (Property):** Sets the type of data to be accumulated. Can be set to Float, Integer, or Vector.
    
- **Domain (Property):** Determines the geometry domain (e.g., Points, Edges, Faces) over which the accumulation is performed.
    
- **Value (Input):** The field of values that will be added together in sequence.
    
- **Group Index (Input):** An integer field used to separate the calculation into multiple independent running totals. Elements with the same Group Index belong to the same accumulation.
    
- **Leading (Output):** The running total where each element includes its own value in the sum. The first element's output is its own value.
    
- **Trailing (Output):** The running total where each element's sum excludes its own value. The first element's output is always zero.
    
- **Total (Output):** A constant value for each group, representing the final sum of all values in that group.
    

**Practical Application:**  
This node is essential for procedurally creating structures where the position of an element depends on the size of all the elements that came before it. A perfect example is modeling a segmented animal, like a centipede, where body segments of varying lengths must be placed one after another without overlapping.

- **The Goal:** To arrange a series of centipede body segments along a curve, where each segment has a random length, and they are all perfectly connected end-to-end.
    
- **The Problem:** If you instance segments on points, they will be placed at the center of those points, causing them to overlap if the segments are longer than the space between the points. You need to find the exact start position for each segment, which requires knowing the combined length of all preceding segments.
    
- **The Solution:** The Accumulate Field node calculates this running total of lengths.
    
    1. Start with a curve defining the centipede's path. Use Resample Curve to create points, one for each segment.
        
    2. Generate a random float value for the length of each segment using a Random Value node.
        
    3. Feed these random lengths into the Value input of an Accumulate Field node.
        
    4. The Trailing output now gives the precise starting offset for each segment. For the first segment, the offset is 0. For the second, the offset is the length of the first. For the third, it's the length of the first + the second, and so on.
        
    5. Use these Trailing values as the Length input for a Sample Curve node. This will find the correct starting point on the main path curve for each segment.
        
    6. Use these sampled positions to set the position of your segment instances.
        

The result is a perfectly formed centipede body where each randomly-sized segment begins exactly where the previous one ended, creating a continuous and organic creature.