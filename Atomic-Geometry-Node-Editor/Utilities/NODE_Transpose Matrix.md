**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Flips a matrix over its main diagonal, swapping its row and column values.

**Key Properties & Settings:**

- **Matrix (Input):** The matrix to be transposed.
    
- **Matrix (Output):_** The resulting transposed matrix.
    

**Practical Application:**  
While an abstract mathematical operation, this node has a critical, high-performance use case: calculating the inverse of a pure rotation. For a matrix that only contains rotation data (no scaling or shearing), its transpose is identical to its inverse but is computationally much faster to calculate. This is useful for converting direction vectors from world space into an object's local space.

Imagine a spider model is oriented on a wall, and you want to simulate wind blowing from a constant world direction (e.g., straight down the X-axis) and see how that wind affects the spider's legs.

- **The Goal:** To calculate the direction of the world-space wind relative to the spider's own coordinate system.
    
- **The Problem:** The spider's rotation is a complex matrix. To know how the world wind vector (1, 0, 0) feels to the spider, you need to apply the inverse of its rotation. Using the Invert Matrix node works, but for pure rotation, Transpose Matrix is more efficient.
    
- **The Solution:**
    
    1. Get the spider object's transformation matrix. Use a Separate Transform node to isolate its Rotation vector.
        
    2. To ensure you have a pure rotation matrix, feed this Rotation vector into a Combine Transform node (leaving Translation at 0 and Scale at 1).
        
    3. Feed this pure rotation matrix into the Transpose Matrix node. The output is now the computationally cheap inverse of the spider's rotation.
        
    4. Define the world wind direction with a Vector node (e.g., (1, 0, 0)).
        
    5. Use a Transform Direction node. Connect the wind vector to the Direction input and the transposed matrix to the Transformation input.
        

The output vector now represents the wind's direction from the spider's point of view. For example, a result of (0, -1, 0) would mean the world wind is blowing directly into the spider's face (assuming its local Y-axis points forward). This local direction vector can then be used to drive procedural animations, like bending the legs away from the wind.