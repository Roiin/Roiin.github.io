- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Write)
    
- **Core Function:** Directly modifies the position of each point or instance in a geometry. It is the fundamental node for displacing, moving, or deforming any mesh.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. Only points where this is True will have their position altered.
        
    - **Position (Socket - Input):** A vector field that defines the absolute new position for each point in world space.
        
    - **Offset (Socket - Input):** A vector field that defines a relative translation to be added to each point's current position. Using this is often more intuitive than setting the absolute position.
        
    - **Geometry (Socket - Output):** The geometry with its points moved to the new locations.
        
- **Practical Application:** This node is the core of procedural modeling and animation. Imagine creating a jellyfish with a pulsating swimming motion.
    
    1. Start with a simple UV Sphere as the jellyfish bell.
        
    2. To create the pulsating effect, you need to move the vertices up and down along their normals (outward from the center).
        
    3. Use a Set Position node. For the Offset input, you need a vector that changes over time.
        
    4. First, get the direction by using a Normal node. This gives a vector pointing outwards for each vertex.
        
    5. Next, get a value that animates. Use a Scene Time node, feed its Seconds output into a Math node set to 'Sine'. This creates a smooth, looping value between -1 and 1.
        
    6. Use a Vector Math node set to 'Scale' to multiply the Normal vector by the animated sine wave value.
        
    7. Plug the result of this 'Scale' operation into the Offset socket of the Set Position node.
        
    8. The result is that every vertex of the sphere will now move back and forth along its own normal, driven by the sine wave, creating a realistic and continuous pulsating animation for the jellyfish bell.