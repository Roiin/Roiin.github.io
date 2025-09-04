- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** For each spline in a curve object, this node outputs a Boolean value that is True if the spline is a closed loop (cyclic) and False if it is an open path with a start and end point.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Cyclic (Socket - Output):** A Boolean field that is True for closed splines and False for open ones.
        
- **Practical Application:** This node allows you to create a single procedural tool that can intelligently build two different kinds of objects, like fences and window frames.
    
    1. You create a node group that takes a curve as input and uses Curve to Mesh to create a profile along it.
        
    2. **The Goal:** If the input curve is an open path, you want to instance a fence post at the start and end. If the input curve is a closed loop (like a rectangle), you want to skip instancing the posts and instead miter the corners of the frame.
        
    3. Use the Is Spline Cyclic node on the input curve. Its Cyclic output will be True for a window frame shape and False for a fence path.
        
    4. Use this Boolean output to drive a Switch node.
        
        - The True path (for the window) can contain logic to correctly miter the corners of the profile mesh.
            
        - The False path (for the fence) can contain logic that uses an Endpoint Selection node to instance posts at the start and end of the curve.
            
    5. The result is a single, powerful "Archviz Profiler" tool. The user simply provides a curve, and the tool automatically detects whether it's an open or closed shape and builds the appropriate object without needing the user to check a box or change a setting.