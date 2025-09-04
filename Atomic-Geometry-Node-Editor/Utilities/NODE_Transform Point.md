**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Applies a full 4x4 transformation matrix (location, rotation, and scale) to a position vector.

**Key Properties & Settings:**

- **Vector (Input):** The position vector of a point to be transformed.
    
- **Transformation (Input):** The 4x4 matrix that defines the transformation.
    
- **Vector (Output):** The new position of the point after the transformation.
    

**Practical Application:**  
This node is the fundamental way to move points from a local coordinate system to a world coordinate system. It's the procedural equivalent of parenting. Imagine you are creating a swarm of particles, like bees, that need to follow and orient themselves around a central, animated "queen bee" object.

- **The Goal:** To have a cloud of procedurally generated bee particles move, rotate, and scale along with a specific target object (the queen).
    
- **The Problem:** If you generate the bee particles within a static volume, they will remain in that volume even if the queen bee object moves away. You need a way to make the entire particle system's coordinate space dependent on the queen's transformation.
    
- **The Solution:** Use the Transform Point node to move the locally-defined particle positions into the queen's moving coordinate space.
    
    1. First, generate the initial positions for your bee particles. This could be a Mesh Cube with points distributed inside it. These points exist in local space around the origin. Get their Position field.
        
    2. Use an Object Info node to get the transformation matrix of your animated "queen bee" object. This matrix contains the queen's current location, rotation, and scale in the world.
        
    3. Use a Transform Point node.
        
        - Connect the Position of your particles to the Vector input.
            
        - Connect the queen's transformation matrix to the Transformation input.
            
    4. The Vector output now gives the correct world-space position for each particle, as if it were parented to the queen.
        
    5. Use a Set Position node on your original particle geometry and feed this new vector into its Position socket.
        

Now, as you animate the queen bee object—moving, rotating, or scaling it—the entire swarm of particles will follow along perfectly, maintaining its shape relative to its leader.