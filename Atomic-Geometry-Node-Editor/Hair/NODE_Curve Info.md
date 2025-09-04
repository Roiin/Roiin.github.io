**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Read)

**Core Function:** Provides access to various data attributes about each individual hair curve, such as its length, index, and direction.

**Key Properties & Settings:**

- **Curve Index (Output):** The sequential index of each curve within the geometry component.
    
- **Length (Output):** The total arc-length of each curve.
    
- **Direction (Output):** A normalized vector pointing from the root (start point) to the tip (end point) of each curve.
    
- **Random (Output):** A stable, random vector assigned to each individual curve.
    
- **Surface UV (Output):** The 2D UV coordinate on the source surface mesh where the root of the curve is attached.
    

**Practical Application:**  
This node is a fundamental data source, allowing you to make procedural decisions based on the properties of each hair. For example, you can use the Length output to vary an effect based on how long a hair is. Imagine creating fur for a rhino where you want the longer hairs (e.g., on the tail tuft) to be a lighter color than the short body fur.

- **The Goal:** To procedurally assign a "sun-bleached" material to the longest hairs on a rhino model, while keeping the shorter body hairs dark.
    
- **The Problem:** You need a way to numerically distinguish between "long" and "short" hairs to create a selection mask for the material.
    
- **The Solution:** The Curve Info node provides the necessary length data.
    
    1. After all hair generation and deformation, add a Curve Info node.
        
    2. Take the Length output, which is a float field containing the length of every hair.
        
    3. Use a Compare node to check if the Length is Greater Than a certain threshold (e.g., 0.1 meters).
        
    4. The Result of the comparison is a Boolean selection that is True only for the hairs that are longer than your threshold.
        
    5. Feed this Boolean selection into the Selection input of a Set Material Index node. You can now assign a different material index to the long hairs.
        

This allows you to create sophisticated, data-driven material and grooming effects that respond to the geometric properties of the hair itself.