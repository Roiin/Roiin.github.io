**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Converter

**Core Function:** Performs a wide variety of mathematical operations on 3D vectors.

**Key Properties & Settings:**

- **Vector/Value (Output):** The output of the node. Some operations (like Add) output a Vector, while others (like Dot Product or Length) output a single numerical Value.
    
- -**Operation (Property):** A large dropdown menu that selects the function to be performed, dynamically changing the node's inputs and outputs.
    
- **Common Operations:**
    
    - **Basic Arithmetic:** Add, Subtract, Multiply. Add is frequently used to offset or mix texture coordinates with a noise texture, creating distortion.
        
    - **Scalar Functions:** Length calculates the distance of a vector from the origin (0,0,0). Distance calculates the distance between two input vectors.
        
    - **Directional Functions:** Normalize takes a vector of any length and gives it a length of 1, preserving its direction. Dot Product calculates the angular relationship between two vectors. Cross Product calculates a third vector perpendicular to the two inputs.
        
    - **Rounding:** Snap rounds a vector to the nearest multiple of another vector, which is essential for creating procedural grids and tiled patterns.
        

**Practical Application:**  
This node is the universal tool for manipulating texture coordinates and other vector data. The Add operation is fundamental for creating procedural distortion, which is key to making clean patterns look more organic, like adding wobble to **wood grain**.

The problem with a basic procedural wood grain (made by stretching a Noise Texture) is that the grain lines are often perfectly straight and parallel, which can look artificial. You need to add a subtle, large-scale waviness to them. The Vector Math node is the perfect solution.

1. Start with your stretched texture coordinates that you're using to create the straight wood grain.
    
2. Add a second, larger-scale Noise Texture (set its Scale to a low value). This will be our "distortion map."
    
3. Add a Vector Math node and set its Operation to Add.
    
4. Connect your original, straight-grain texture coordinates into the top vector slot.
    
5. Connect the Color output of the large-scale Noise Texture into the bottom vector slot. (Note: It's good practice to subtract 0.5 from the noise color first to make it centered around zero, preventing the texture from just drifting in one direction).
    
6. Connect the Vector output of the Vector Math node to your final wood grain texture.
    
7. The result is that the large, slow-moving noise pattern is now being added to the original coordinates, effectively warping them before they are used. This transforms the perfectly straight grain lines into gently waving, organic lines, dramatically increasing the material's realism.