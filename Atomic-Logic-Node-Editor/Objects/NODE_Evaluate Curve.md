- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 5 - Curves
    
- **Core Function:** Calculates the world-space coordinate of a single point at a specific position along the length of a curve.
    
- **Key Properties & Settings:**
    
    - **Input (Curve):** The curve object to evaluate.
        
    - **Input (Factor):** A float value from 0.0 (start of the curve) to 1.0 (end of the curve) that determines the position to evaluate.
        
    - **Output (Vector):** The calculated vector position of the point on the curve.
        
- **Practical Application:** The core of any system for moving an object along a path. By animating the "Factor" value over time, you can make an object (like a character, a vehicle, or a camera) travel smoothly along the curve.