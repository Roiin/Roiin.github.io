- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 5 - Curves
    
- **Core Function:** Generates a list of vector points evenly distributed along the length of a curve object.
    
- **Key Properties & Settings:**
    
    - **Input (Refresh):** A Boolean that, when set to true, forces the node to recalculate the point distribution.
        
    - **Input (Curve):** The curve object on which to distribute the points.
        
    - **Setting (Show Debug):** A checkbox to visually display the generated points in the viewport for debugging purposes.
        
    - **Setting (Custom Amount):** A checkbox that likely enables an input to specify the exact number of points to generate.
        
    - **Output (Points):** A list containing the vector positions of the generated points.
        
    - **Output (Done):** A flow control pulse that activates after the points have been calculated.
        
- **Practical Application:** Used for procedural placement of objects along a path. For example, automatically placing fence posts along a curved line or setting up spawn points for a wave of enemies along a defined route.