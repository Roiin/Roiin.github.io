**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Deconstructs a 4x4 transformation matrix into its three high-level components: a translation vector, a rotation vector, and a scale vector.

**Key Properties & Settings:**

- **Transform (Input):** The transformation matrix to be separated.
    
- **Translation (Output):** The position component of the matrix as a vector.
    
- **Rotation (Output):** The Euler rotation component of the matrix as a vector (in radians).
    
- **Scale (Output):** The scale component of the matrix as a vector.
    

**Practical Application:**  
This node is the direct inverse of Combine Transform and is crucial for when you need to use only one aspect of an object's transformation. For example, imagine you have a procedurally animated animal, like a spider, and you want to create a simple, flat shadow decal on the ground that follows its movement but ignores its complex body rotations.

- **The Goal:** To create a simple shadow plane that copies the spider's X and Y position but remains flat on the ground and at a constant size.
    
- **The Problem:** The spider's overall transformation is a single matrix that includes location, rotation, and scale. If you apply this entire matrix to a simple plane, the plane will tilt, rotate, and scale along with the spider's body, which is not how a shadow on a flat surface behaves.
    
- **The Solution:** The Separate Transform node allows you to isolate only the translation data.
    
    1. Use an Object Info node to get the transformation matrix of the animated spider.
        
    2. Connect this matrix to the Transform input of the Separate Transform node.
        
    3. The node will output three separate vectors. You are only interested in the Translation vector. Ignore the Rotation and Scale outputs.
        
    4. Take this Translation vector and use it to control the position of your shadow plane geometry (e.g., a Grid primitive). To ensure it stays flat on the ground, you could use Separate XYZ on the vector and then Combine XYZ to rebuild it with a Z value of 0.
        
    5. Feed this final position vector into a Set Position node affecting the shadow plane.
        

As the spider walks and animates, the shadow plane will now follow its position on the ground perfectly, but it will remain flat and un-scaled, creating a much more believable and computationally cheap ground shadow.