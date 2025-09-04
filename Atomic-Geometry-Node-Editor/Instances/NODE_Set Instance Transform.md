- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** Directly sets the entire transform (location, rotation, and scale) of existing instances using a 4x4 transformation matrix. Unlike the individual Translate/Rotate/Scale Instances nodes, this is not an additive operation; it replaces the existing transform of each selected instance.
    
- **Key Properties & Settings:**
    
    - **Instances (Socket - Input):** The geometry containing the instances to be transformed.
        
    - **Selection (Socket - Input):** A Boolean mask. Only the transforms of selected instances will be set.
        
    - **Transform (Socket - Input):** A 4x4 matrix field that provides the complete new transform for each instance. This can be constructed from separate vectors using a Compose Matrix node.
        
    - **Instances (Socket - Output):** The geometry with its instances set to the new transforms.
        
- **Practical Application:** This node is ideal when you need to precisely transfer the transform from one set of objects to another, like creating a "ghost" or "trail" effect for an animated animal.
    
    1. Imagine you have a complex, animated animal (like a running wolf) and you want to leave a trail of static, ghost-like copies of it at certain frames.
        
    2. You can create a point cloud where each point's ID corresponds to a frame number where you want to leave a trail (e.g., points with ID 10, 20, 30).
        
    3. On a separate object, use a Geometry Sequence node (an experimental feature, but illustrates the principle) or similar technique to access the wolf's mesh and its world transform matrix at a specific frame.
        
    4. You would then instance your "ghost" wolf model onto your point cloud.
        
    5. Use the Set Instance Transform node on these ghost instances. For the Transform input, you would sample the animated wolf's transform matrix at the frame number corresponding to each point's ID.
        
    6. The result is that the instance at point #10 will have its transform perfectly set to match the animated wolf's transform at frame 10. The instance at point #20 will match frame 20, and so on. This creates a perfect "echo" or "strobe" effect of the animation, which would be very difficult to achieve with the additive transform nodes.