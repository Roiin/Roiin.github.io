- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Sample)
    
- **Core Function:** Acts like a lookup tool. It takes an index number, goes to a separate target geometry, finds the element at that index, and retrieves a specified attribute value (like its position or color).
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry to read the data from.
        
    - **Value (Socket - Input):** The attribute or field to be read from the target geometry (e.g., Position, Normal, or a custom attribute).
        
    - **Index (Socket - Input):** The specific index number(s) to look up on the target geometry.
        
    - **Domain (Property):** The attribute domain (Point, Edge, Face, etc.) on the target geometry from which to sample the data.
        
    - **Clamp (Property):** If True, any out-of-bounds index (e.g., asking for index 50 in a 10-element list) will be clamped to the last valid index. If False, it will output a default value (e.g., zero).
        
    - **Value (Socket - Output):** The data that was retrieved from the target geometry at the specified index.
        
- **Practical Application:** This is perfect for creating "follow the leader" behavior in a group of animals. Imagine you want to create a static pose of a school of fish swimming in a line, where each fish is oriented towards the one in front of it.
    
    1. Start with a Mesh Line primitive, which gives you a series of points with ordered indices (0, 1, 2, ...). These points will represent your fish.
        
    2. For each point at index i, you need to find the position of the point in front of it, which is at index i - 1.
        
    3. Use the Sample Index node. The Geometry is the Mesh Line itself. The Value you want to read is its Position. For the Index input, you provide the Index node minus 1. (Make sure to enable Clamp so the first fish doesn't cause an error).
        
    4. The Value output of this node now gives every fish the exact position of the fish ahead of it.
        
    5. You can use this "target position" along with the fish's own position to calculate a direction vector, and then use an Align Euler to Vector node to orient each instanced fish model, making them all appear to follow one another in a perfect line.