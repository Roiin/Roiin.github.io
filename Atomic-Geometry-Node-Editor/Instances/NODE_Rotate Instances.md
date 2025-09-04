- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** Applies a rotation to existing instances. This is a more efficient and targeted way to rotate instances compared to realizing them and using a Transform Geometry node.
    
- **Key Properties & Settings:**
    
    - **Instances (Socket - Input):** The geometry containing the instances to be rotated.
        
    - **Selection (Socket - Input):** A boolean mask. Only selected instances will be rotated.
        
    - **Rotation (Socket - Input):** An Euler rotation value that will be added to the existing rotation of each instance.
        
    - **Pivot Point (Socket - Input):** A vector defining the center of rotation for each instance. By default, this is the instance's origin.
        
    - **Local Space (Socket - Input):** A boolean. If True, the rotation is applied relative to the instance's own orientation (e.g., "roll" or "pitch"). If False, the rotation is applied relative to the world axes.
        
    - **Instances (Socket - Output):** The geometry with its instances rotated.
        
- **Practical Application:** This node is perfect for adding secondary, animated rotation to a group of instances, like making a flock of birds bank into a turn.
    
    1. First, you create a flock of birds instanced on a point cloud. You use an Align Euler to Vector node to make each bird point in its direction of travel, which is their primary rotation.
        
    2. **The Goal:** As the flock collectively turns a corner, you want all the birds to "bank" (roll on their local axis) into the turn.
        
    3. You can create a custom attribute or use a driver to determine the "bank angle" for the entire flock based on the curve of their flight path. This will be a single, animated float value.
        
    4. Use the Rotate Instances node. Set Local Space to True.
        
    5. For the Rotation input, use a Combine XYZ node. Feed your animated "bank angle" into the appropriate axis for rolling (e.g., the Y-axis).
        
    6. The result is that the Rotate Instances node adds this banking rotation on top of the existing forward-facing rotation. The birds will continue to point in their direction of travel, but will also realistically roll into and out of turns as a cohesive group, all controlled by a single animated value.