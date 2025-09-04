- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** For each top--level instance, this node outputs its final scale as an XYZ vector.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Scale (Socket - Output):** An XYZ vector field representing the final scale of each instance.
        
- **Practical Application:** This node is ideal for transferring scale information to other attributes, like a particle system's size or a shader's effect radius. Imagine you have a field of instanced "magical trees" with varied, randomized scales. You want each tree to emit glowing particles, and you want larger trees to emit larger particles.
    
    1. First, you generate your forest of instanced trees with randomized Scale.
        
    2. Use the Instances to Points node to convert your tree instances into a point cloud. This automatically transfers the scale attribute to the points.
        
    3. You now want to spawn your glowing particle instances onto these points. Use a second Instance on Points node for this.
        
    4. Use the Instance Scale node to read the scale attribute from the points (which originally came from the trees).
        
    5. You can take the average of the X, Y, and Z components of this scale vector to get a single float value representing the tree's overall size.
        
    6. Connect this calculated average size directly into the Scale input of your second Instance on Points node (the one creating the particles).
        
    7. The result is a particle system where the size of the emitted particles is directly proportional to the size of the tree they are coming from. Large trees will have large, bright auras, while small trees will have small, subtle ones, creating a cohesive and visually logical effect.