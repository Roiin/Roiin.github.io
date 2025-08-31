- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Smoothly rotates an object to match a target orientation over time.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input.
        
    - **Condition (Socket):** A boolean input.
        
    - **Object (Socket):** The object to rotate.
        
    - **Target (Socket):** A 3D vector input representing the target Euler rotation in degrees.
        
    - **Factor (Socket):** A float (0.0 to 1.0) controlling the interpolation speed. A lower value means a slower, smoother rotation.
        
- **Practical Application:** Useful for any smooth, non-instantaneous rotation. For example, smoothly rotating a turret to face a new direction, or gradually turning a security camera.