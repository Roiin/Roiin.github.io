- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Generates a point cloud from an input curve, with options to control the number and spacing of the points. It also conveniently outputs the curve's Tangent, Normal, and a combined Rotation at each generated point, making it perfect for instancing.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve to be converted into points.
        
    - **Mode (Property):** The method for point generation:
        
        - **Evaluated:** Creates a point for each of the curve's existing evaluated points. The result is unevenly spaced on Bézier/NURBS curves.
            
        - **Count:** Distributes a specific, user-defined number of points evenly along the curve's length.
            
        - **Length:** Creates points spaced apart by a specific, user-defined distance.
            
    - **Points (Socket - Output):** The resulting point cloud geometry.
        
    - **Tangent (Socket - Output):** The forward direction of the curve at each generated point.
        
    - **Normal (Socket - Output):** The "up" direction of the curve at each generated point.
        
    - **Rotation (Socket - Output):** A pre-calculated Euler rotation that aligns objects to the curve's tangent and normal, ready for direct use in instancing.
        
- **Practical Application:** This node is ideal for creating segmented creatures that follow a path, like a caterpillar.
    
    1. First, draw a single, winding curve to define the caterpillar's path and pose.
        
    2. Use the Curve to Points node. Set the Mode to 'Length'. The Length value now controls the spacing between the caterpillar's body segments. A smaller value creates a longer caterpillar with more segments.
        
    3. Connect the Points output to an Instance on Points node. For the Instance, use a simple sphere, which will represent one body segment.
        
    4. Connect the Rotation output directly to the Rotation input of the Instance on Points node.
        
    5. The result is a perfectly formed caterpillar. A sphere is instanced at regular intervals along the curve, and each sphere is automatically rotated to follow the curve's twists and turns. You can easily animate the entire creature simply by animating the underlying curve.