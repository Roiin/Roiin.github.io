- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** Collapses a set of instances down to a simple point cloud, where each point represents the origin (pivot point) of a single top-level instance. Critically, any attributes on the instance domain are transferred to the newly created points.
    
- **Key Properties & Settings:**
    
    - **Instances (Socket - Input):** The source geometry containing the instances to be converted.
        
    - **Selection (Socket - Input):** A boolean mask. Only selected instances will be converted into points.
        
    - **Position (Socket - Input):** An optional vector field to override the position of the created points. By default, it uses the instance's position.
        
    - **Radius (Socket - Input):** A float field to set the radius attribute for the output points, which controls their display size in the viewport.
        
    - **Points (Socket - Output):** The resulting point cloud.
        
- **Practical Application:** This node is perfect for creating secondary effects that are based on the final positions of instanced objects. Imagine you have created a procedural animal, like a spider, using instancing. The main body is a sphere, and you have instanced eight leg objects around it.
    
    1. **The Goal:** You now want to connect the spider to a surface with a single strand of web silk, originating from the spider's main body.
        
    2. **The Problem:** Your current geometry is a collection of nine separate instances (1 body + 8 legs). You only care about the final location of the body instance.
        
    3. **The Solution:**
        
        - First, separate the body instance from the leg instances (e.g., based on an ID attribute you assigned earlier).
            
        - Feed only the body instance into the Instances to Points node. The output is now a single point at the exact final location of the spider's body.
            
        - You can now use this single point as the Start position for a Curve Line node. The End position can be found by raycasting down to the floor.
            
        - The result is a single strand of web silk that is guaranteed to originate from the center of the spider, no matter how you move, rotate, or scale the main spider object. The node allowed you to "forget" the complexity of the instanced spider and just get its final summary position.