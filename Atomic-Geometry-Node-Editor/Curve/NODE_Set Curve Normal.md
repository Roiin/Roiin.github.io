- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Write)
    
- **Core Function:** Sets the calculation method used to determine the "up" vector (the normal) along a curve's length. This is crucial for controlling the orientation of geometry extruded along the curve, preventing unwanted twisting.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The curve geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. The normal calculation method will only be changed on splines where this is True.
        
    - **Mode (Property):** The core control for the node:
        
        - **Minimum Twist:** This is the default and most common mode. It intelligently calculates the normals to minimize any twisting as the curve bends and turns in 3D space.
            
        - **Z-Up:** Forces the normals to be as aligned with the global Z-axis as possible, which is useful for things like roads that should remain flat.
            
        - **Free:** Allows you to provide your own custom normal vectors via a new Normal input socket. This is for advanced, specific control.
            
    - **Curve (Socket - Output):** The curve, now with its new normal calculation setting.
        
- **Practical Application:** This node is essential for creating predictable and stable geometry from curves, like a roller coaster track.
    
    1. First, you create a complex, winding Bézier curve for the track's path, including loops and banked turns.
        
    2. You use a Curve to Mesh node to extrude a track profile (like a simple square) along this path.
        
    3. **The Problem:** Without controlling the normals, the track might twist and flip unpredictably, especially as it goes through a vertical loop. The cross-section of the track could suddenly turn upside down.
        
    4. **The Solution:** Insert a Set Curve Normal node before the Curve to Mesh node. Set its Mode to 'Minimum Twist'.
        
    5. This forces Blender to use a more robust calculation that keeps the track's orientation consistent and smooth throughout the entire path. The unwanted flipping is eliminated, and the banked turns you designed with the curve's Tilt property will be preserved correctly.