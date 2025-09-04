- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** Moves (translates) existing instances by a given vector amount. This is an additive operation; the Translation vector is added to the instance's current position.
    
- **Key Properties & Settings:**
    
    - **Instances (Socket - Input):** The geometry containing the instances to be moved.
        
    - **Selection (Socket - Input):** A boolean mask. Only selected instances will be moved.
        
    - **Translation (Socket - Input):** A vector that provides the direction and distance to move each instance.
        
    - **Local Space (Socket - Input):** A boolean. If True, the translation is applied relative to the instance's own orientation (e.g., "move forward" or "strafe left"). If False, the translation is applied along the world axes (X, Y, Z).
        
    - **Instances (Socket - Output):** The geometry with its instances translated.
        
- **Practical Application:** This node is perfect for animating simple, non-deforming movement, like a swarm of bees or particles.
    
    1. First, you create a swarm of bee instances distributed inside a volume.
        
    2. **The Goal:** You want the entire swarm to drift slowly in one direction, while each individual bee also has its own random, buzzing motion.
        
    3. You can achieve the individual buzzing by adding an animated Noise Texture to the original positions of the points before instancing.
        
    4. To create the collective drift, use the Translate Instances node after the bees have been instanced.
        
    5. For the Translation input, you can use a Combine XYZ node. Animate the X value to increase over time (e.g., by connecting it to the Seconds output of a Scene Time node).
        
    6. The result is two layers of motion. The underlying points are buzzing randomly, and the Translate Instances node adds a constant, global movement on top of that. This is a very efficient way to create complex-looking motion, as you are only moving the lightweight instances, not recalculating the positions of thousands of points every frame.