**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Constrains an input value to a specified range, forcing it to be no lower than a minimum and no higher than a maximum.

**Key Properties & Settings:**

- **Value (Input):** The numerical value (float, integer, or vector) to be constrained.
    
- **Min (Input):** The lower bound of the range. The output will not be less than this value.
    
- **Max (Input):** The upper bound of the range. The output will not be greater than this value.
    
- **Clamp Type (Property):** Defines the clamping method, typically Min Max, which enforces the specified range.
    

**Practical Application:**  
The Clamp node is crucial for controlling the influence of procedural textures to prevent extreme or undesirable effects. Imagine you are adding a bumpy, organic texture to the skin of a rhinoceros model by displacing its vertices with a noise texture.

- **The Goal:** To create a random, bumpy skin texture on a rhino, but keep the bumps within a subtle and believable size range.
    
- **The Problem:** A raw Noise Texture outputs values that can be unpredictable. When used to drive a displacement, this can lead to some vertices being pushed too far out, creating unrealistic spikes, or even being pushed inward (inverted), creating holes in the mesh.
    
- **The Solution:** Use the Clamp node to tame the output of the noise texture before it affects the geometry.
    
    1. On your rhino mesh, use a Set Position node to displace the vertices. The displacement vector can be the vertex Normal scaled by a noise texture.
        
    2. Take the Factor output from a Noise Texture node.
        
    3. Connect this Factor into the Value input of a Clamp node.
        
    4. Set the Min value to 0.05. This ensures that even the darkest parts of the noise texture produce a slight outward bump, preventing any inversion.
        
    5. Set the Max value to 0.2. This caps the highest values of the noise, preventing any single vertex from creating a large, unnatural spike.
        
    6. Use the Result from the Clamp node to scale the Normal vector and plug that into the Offset of the Set Position node.
        

The result is a rhino with a naturally bumpy hide. The texture is still random and organic, but the Clamp node guarantees that the effect stays within the controlled, artistic limits you have defined.