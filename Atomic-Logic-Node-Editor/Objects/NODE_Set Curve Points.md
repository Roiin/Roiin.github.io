- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 5 - Curves
    
- **Core Function:** Modifies a curve object in real-time by replacing its control points with a new list of vector positions.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Curve):** The target curve object to be modified.
        
    - **Input (Points):** A list of vectors that will become the new control points for the curve.
        
    - **Output (Done):** A flow control pulse that activates after the curve has been updated.
        
- **Practical Application:** Allows for dynamic and procedural generation of paths. For example, creating a hanging rope or chain that sags dynamically, or generating a path for a projectile that needs to bend around obstacles.