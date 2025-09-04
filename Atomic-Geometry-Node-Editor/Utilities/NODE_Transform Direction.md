**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Applies the rotational and scale components of a transformation matrix to a direction vector, ignoring any translation.

**Key Properties & Settings:**

- **Direction (Input):** The vector to be transformed. This typically represents a direction like a surface normal, not a position.
    
- **Transformation (Input):** The 4x4 matrix whose rotation and scale will be applied.
    
- **Direction (Output):** The resulting transformed vector.
    

**Practical Application:**  
This node is crucial for correctly updating direction vectors, like surface normals, after a mesh has been transformed. Imagine you are procedurally generating a tree, and after creating the trunk and branches, you apply a matrix transformation to bend the entire tree to simulate wind.

- **The Goal:** To correctly orient leaves on the surface of the now-bent tree.
    
- **The Problem:** The original Normal vectors of the straight tree are no longer correct for the bent tree. If you use the old normals to align your leaves, they will point out at incorrect angles, not perpendicular to the new, curved surface. The Transform Point node is also incorrect, as it would apply the matrix's translation, which makes no sense for a direction vector.
    
- **The Solution:** The Transform Direction node applies only the rotational part of the transformation to the normals.
    
    1. Before deforming the tree, use a Capture Attribute node to store the original Normal vector of the mesh.
        
    2. Create the matrix that will bend the tree (e.g., using Combine Transform to apply a rotation).
        
    3. Use a Transform Geometry node to apply this matrix, bending the tree's geometry.
        
    4. Now, take the original Normal attribute you captured.
        
    5. Feed this Normal into the Direction input of the Transform Direction node.
        
    6. Feed the same bending matrix into the Transformation input.
        
    7. The Direction output is the new, correct normal vector for each point on the bent surface. You can now use this vector with a node like Align Euler to Vector to orient your instanced leaves so they point perfectly outward from the bent branches.