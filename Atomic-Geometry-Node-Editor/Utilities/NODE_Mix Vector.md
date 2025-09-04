**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Vector)

**Core Function:** Blends between two vectors (A and B) using a float Factor to control the interpolation.

**Key Properties & Settings:**

- **Factor Mode (Property):**
    
    - **Uniform:** A single float value is used as the Factor for all three axes (X, Y, Z) of the vectors.
        
    - **Non-Uniform:** Allows for a vector input as the Factor, enabling different mix amounts for each axis independently.
        
- **Factor (Input):** Controls the amount of mixing. A factor of 0.0 will output Vector A, a factor of 1.0 will output Vector B, and 0.5 will output an even mix.
    
- **A (Input):** The first vector in the mix.
    
- **B (Input):** The second vector in the mix.
    
- **Clamp Factor (Checkbox):** When enabled, it limits the Factor to the 0.0 to 1.0 range. Disabling this allows for extrapolation, where the mixing can go beyond the original vectors.
    
- **Result (Output):** The final blended vector.
    

**Practical Application:**  
This node is extremely powerful for creating procedural transitions between two different states of a mesh's geometry. For example, imagine you are modeling a procedural tree that can change with the seasons, showing its branches drooping under the weight of winter snow.

- **The Goal:** To create a slider that smoothly transitions the tree's branches from their normal, upward-reaching state to a heavy, drooping state.
    
- **The Problem:** You have the original positions of all the vertices for the "summer" tree. You have also calculated the desired final positions for a "winter" tree where the branches are bent downwards. You need a way to create a smooth, controllable blend between these two poses.
    
- **The Solution:** The Mix Vector node is ideal for interpolating between two sets of position vectors.
    
    1. Start with your base tree geometry.
        
    2. Capture the original vertex positions using a Capture Attribute node. This is your **"Summer"** state (Vector **A**).
        
    3. Create a second set of vertex positions where the branches are bent down (e.g., by using a Set Position with a noise texture affecting the Z-axis). This is your **"Winter"** state (Vector **B**).
        
    4. Use a Mix node set to Vector type.
        
    5. Connect the **"Summer"** positions to input A.
        
    6. Connect the **"Winter"** positions to input B.
        
    7. Create a single Value input (or a slider in your modifier) named "Winter Weight" that goes from 0.0 to 1.0. Connect this to the Factor.
        
    8. Feed the Result of the Mix node into a final Set Position node.
        

Now, as you drag the "Winter Weight" slider from 0.0 to 1.0, the tree's branches will smoothly and procedurally droop, giving a convincing effect of snow accumulating on them.