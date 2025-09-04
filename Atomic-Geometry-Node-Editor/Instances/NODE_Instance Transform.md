- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** For each top-level instance, this node outputs its complete transformation (location, rotation, and scale) packaged together into a single 4x4 matrix. This is often used with a Decompose Matrix node to analyze the final state of instances.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Transformation (Socket - Output):** A 4x4 matrix field containing the full transform for each instance.
        
- **Practical Application:** This node is perfect for analyzing the final state of instances to make decisions. Imagine you have a forest of procedurally generated trees with randomized scales on all three axes, and you want to delete any trees that have become too "squashed" (i.e., their vertical scale is too small).
    
    1. First, you generate your forest of instanced trees with varied scales.
        
    2. Use the Instance Transform node to get the final transform matrix for each tree instance.
        
    3. Connect this Transformation output to a Decompose Matrix node. This breaks the matrix back down into its separate Location, Rotation, and Scale vector components.
        
    4. Take the Scale vector output and use a Separate XYZ node to isolate the Z component (the vertical scale).
        
    5. Use a Compare node to check if this Z value is less than a certain threshold (e.g., 0.5).
        
    6. The Boolean result of this comparison is a selection that is True for every tree that is too short and squashed.
        
    7. Feed this selection into a Delete Geometry node (with the Domain set to 'Instance'). The result is a forest where all the unnaturally short trees have been automatically culled.