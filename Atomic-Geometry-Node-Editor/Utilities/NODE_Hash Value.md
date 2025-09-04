**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Generates a pseudo-random integer (a "hash") based on an input value and a seed.

**Key Properties & Settings:**

- **Data Type (Property):** Sets the type of the Value input. This can be a float, integer, vector, color, string, and more.
    
- **Value (Input):** The source data that will be converted into a hash. The same input value will always produce the same hash.
    
- **Seed (Input):** An integer that offsets the hash generation, allowing you to get different random results from the same input value.
    
- **Hash (Output):** The resulting pseudo-random integer.
    

**Practical Application:**  
This node is excellent for creating stable randomness where the outcome for a specific element should not change even when other elements are added or removed. Imagine you are procedurally generating a forest by scattering points. You want the type of tree at any given location to be consistent.

- **The Goal:** To assign a random tree type (e.g., pine, oak, or birch) to each point in a forest, ensuring that the tree at a specific coordinate, like (10, 5, 0), is always an oak, even if you change the total number of trees.
    
- **The Problem:** Using a standard Random Value node with the point's Index as the ID is unstable. If you add or delete a point, the indices of all subsequent points are re-calculated, causing the entire forest layout to change randomly, which disrupts the creative process.
    
- **The Solution:** Use the Hash Value node with the point's unchanging Position as the input.
    
    1. After distributing your points for the forest, get the Position field.
        
    2. Connect the Position vector into the Value input of the Hash Value node.
        
    3. The Hash output is a large, unique-looking integer for each point based on its location.
        
    4. To use this as an index for your tree collection, you need to constrain its range. Use a Math node set to Modulo. If you have 3 tree types, calculate Hash % 3. This will result in a stable integer of 0, 1, or 2 for each point.
        
    5. Feed this result into the Instance Index socket of your Instance on Points node.
        

Now, the type of tree at any location is determined by its coordinates, not by its index in the point list. You can change the density of the forest, and the existing trees will remain the same type, providing a much more stable and predictable workflow.