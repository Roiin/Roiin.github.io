- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Primitives)
    
- **Core Function:** Generates a closed, circular poly spline. It has two modes for defining the circle: either numerically with a Radius or spatially with three Points that lie on its circumference.
    
- **Key Properties & Settings:**
    
    - **Mode (Property):**
        
        - **Radius:** Defines the circle with a simple Radius value, centered at the object's origin.
            
        - **Points:** Defines the circle by calculating the unique circle that passes through three provided Point vectors.
            
    - **Resolution (Socket - Input):** An integer that controls how many vertices the circle will have. A value of 3 creates a triangle, 4 a square, etc.
        
    - **Radius (Socket - Input):** In Radius mode, this float controls the circle's size.
        
    - **Curve (Socket - Output):** The generated circular curve.
        
    - **Center (Socket - Output):** In Points mode, this outputs the calculated center of the circle.
        
- **Practical Application:** The Curve Circle is the most common Profile Curve used with the Curve to Mesh node to create pipes, ropes, tentacles, and tree branches.
    
    1. First, you create a long, winding Bézier curve to be the main path of an octopus tentacle. You use Set Curve Radius to make it taper from thick to thin.
        
    2. Use the Curve Circle node. Set its Resolution to something like 10 to create a smooth, round profile.
        
    3. Connect this Curve Circle to the Profile Curve input of a Curve to Mesh node.
        
    4. Connect the main tentacle path to the Curve input of the Curve to Mesh node.
        
    5. The result is a fully 3D tentacle mesh. Its path is defined by your main curve, and its cross-sectional shape is a circle defined by the Curve Circle node. You can easily make the tentacle more square or triangular simply by changing the Resolution on the Curve Circle node.