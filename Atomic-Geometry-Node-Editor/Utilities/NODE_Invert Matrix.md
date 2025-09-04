**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Calculates the inverse of a transformation matrix, which effectively "undoes" the original transformation.

**Key Properties & Settings:**

- **Matrix (Input):** The 4x4 matrix to be inverted.
    
- **Matrix (Output):** The resulting inverted matrix. If the input matrix is not invertible (e.g., if it has a scale of zero), this will output an identity matrix.
    
- **Invertible (Output):** A boolean value that is True if the matrix was successfully inverted and False otherwise. This is useful for preventing errors in a node tree.
    

**Practical Application:**  
The primary use of this node is to transform coordinates from world space into an object's local space. This is essential for making procedural textures or effects "stick" to a deforming or animated object. Imagine you are applying a procedural noise pattern to the skin of a spider, and you need that pattern to move and stretch along with the spider's animation.

- **The Goal:** To make a Noise Texture evaluate in the spider's local coordinate system, so the texture deforms with the animated character.
    
- **The Problem:** By default, a Noise Texture exists in static world space. If you animate the spider object (moving, rotating, or scaling it), the spider will simply move through the fixed 3D texture, creating an unnatural "swimming" effect.
    
- **The Solution:** You must transform the coordinates used to sample the texture from world space into the spider's moving local space.
    
    1. Use an Object Info node to get the transformation matrix of your animated spider object. This matrix transforms points from the spider's local space to world space.
        
    2. Feed this matrix into the Invert Matrix node. The output is a new matrix that does the opposite: it transforms points from world space back to the spider's local space.
        
    3. Take the Position field of the geometry you want to texture.
        
    4. Use a Transform Point node (found in the Matrix menu) and transform the Position using the inverted matrix from step 2.
        
    5. Connect the output of the Transform Point node into the Vector input of your Noise Texture.
        

Now, the noise texture is being sampled in a coordinate system that is locked to the spider object. When the spider moves, rotates, or scales, the texture coordinates move with it, ensuring the pattern sticks to the surface and deforms naturally with the animation.