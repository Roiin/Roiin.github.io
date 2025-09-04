- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Gizmo)
    
- **Core Function:** Creates a complete 3D transform gizmo (with move, rotate, and scale handles) in the viewport, allowing a user to interactively control the position, orientation, and size of an element.
    
- **Key Properties & Settings:**
    
    - **Value (Socket - Input/Output):** A special socket that connects to the transform data (location, rotation, and scale) that the gizmo will read from and modify.
        
    - **Position (Socket - Input):** A vector that sets the initial center point of the gizmo in the object's local space.
        
    - **Rotation (Socket - Input):** An Euler rotation value that sets the gizmo's initial orientation. (Note: This can be overridden if the viewport's transform orientation is set to 'Global').
        
    - **Gizmo Component Toggles (Properties):** In the sidebar, there are checkboxes to enable or disable the individual move, rotate, and scale components of the gizmo.
        
    - **Transform (Socket - Output):** The gizmo's visual data, which must be joined with the final geometry (using a Join Geometry node) to be visible in the viewport.
        
- **Practical Application:** This is ideal for creating a simple "asset placer." Imagine you have a procedural building and you want to place a door object onto it. You can bring the door in with an Object Info node and use a Transform Geometry node to position it. By driving the Transform Geometry node with the Value output of the Transform Gizmo, a full gizmo appears. You can then interactively drag, rotate, and scale the door directly on the building's surface to find the perfect placement, without ever touching the raw numbers in the nodes. You could disable the 'Scale' property in the sidebar to prevent the user from accidentally resizing the door.