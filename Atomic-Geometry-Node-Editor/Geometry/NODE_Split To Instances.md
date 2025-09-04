- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Splits a geometry into groups based on a shared Group ID attribute and converts each distinct group into a separate, movable instance. This is the primary method for breaking a single continuous mesh into many individual pieces.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry to be split.
        
    - **Selection (Socket - Input):** A Boolean mask to choose which elements will be part of the splitting process.
        
    - **Group ID (Socket - Input):** The critical input. An integer field where all elements with the same integer value are bundled together into the same output instance.
        
    - **Domain (Property):** Specifies the type of element to group and split (Point, Edge, Face, Spline, Instance). Elements not matching the selected domain will be discarded.
        
    - **Instances (Socket - Output):** A list of the newly created instances, one for each unique Group ID.
        
    - **Group ID (Socket - Output):** Outputs the integer Group ID corresponding to each new instance, allowing you to identify and treat each instance differently later on.
        
- **Practical Application:** This node is perfect for creating a shattered glass effect for a window.
    
    1. Start with a heavily subdivided Grid to represent the glass pane.
        
    2. Use a Voronoi Texture to generate a cellular shatter pattern. Sample this texture for each face of the grid to get a unique value for each 'cell' in the pattern. Convert this value to an integer to use as the Group ID.
        
    3. Feed this into the Split to Instances node with the Domain set to 'Face'. The output is now a collection of instances, where each instance is a single, jagged glass shard.
        
    4. To make the window explode, connect the Instances output to a Translate Instances or Transform Instances node. You can then use a Random Value node (or the position of each shard relative to the center) to translate and rotate them outwards, creating a dynamic shattering animation from a single, unbroken plane.