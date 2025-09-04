- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** The primary node for creating instances. It places a copy of a given Instance geometry onto every point of an input Points geometry. This is the foundation for efficiently populating scenes with vast numbers of repeating or varied elements without duplicating the underlying mesh data, ensuring high performance.
    
- **Key Properties & Settings:**
    
    - **Points (Socket - Input):** The geometry (mesh, point cloud, curve) whose points will serve as the locations for the new instances.
        
    - **Selection (Socket - Input):** A boolean mask. An instance will only be created on points where this is True.
        
    - **Instance (Socket - Input):** The source geometry to be instanced. This can be a single object or a collection of instances (e.g., from a Collection Info node).
        
    - **Pick Instance (Property):** A boolean toggle on the node. If True, it treats the Instance input as a list and uses the Instance Index to pick one item from the list for each point. This is essential for creating variation.
        
    - **Instance Index (Socket - Input):** An integer field that specifies which instance to pick from the list when Pick Instance is enabled.
        
    - **Rotation (Socket - Input):** An Euler rotation value applied to each instance, allowing for individual orientation.
        
    - **Scale (Socket - Input):** A vector value that controls the size of each individual instance.
        
    - **Instances (Socket - Output):** The final geometry, now containing the generated instances.
        
- **Practical Application:** This node is fundamental for creating any large-scale natural environment, like a forest.
    
    1. **The Problem:** Placing thousands of individual trees by hand is impossibly tedious, and duplicating the actual tree mesh thousands of times would make the Blender file enormous and the viewport unusably slow.
        
    2. **The Solution:**
        
        - First, create a collection containing several different tree models (e.g., "Pine_01", "Pine_02", "Birch_01"). Use a Collection Info node to bring this into the node tree.
            
        - On your landscape mesh, use a Distribute Points on Faces node to generate thousands of points where the trees will grow. This also conveniently provides a random Rotation for each point.
            
        - Use the Instance on Points node. The Points input comes from the Distribute Points... node.
            
        - Connect the Collection Info node to the Instance input and, crucially, **enable Pick Instance**.
            
        - Connect the Rotation output from Distribute Points... to the Rotation input here.
            
        - Use a Random Value node (e.g., with a range from 0.8 to 1.5) and connect it to the Scale input to give the trees varied sizes.
            
    3. **The Result:** A vast, diverse forest is generated instantly. For each point, the node randomly picks one of the tree models from the collection, gives it a random rotation, and a random scale. Because they are lightweight instances, not full copies of the mesh, the scene remains fast and responsive, even with thousands of trees.