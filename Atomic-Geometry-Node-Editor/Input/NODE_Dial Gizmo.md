- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Gizmo)
    
- **Core Function:** Creates a circular, interactive "dial" gizmo in the 3D viewport, allowing a user to visually control and animate an angle value directly on the object.
    
- **Key Properties & Settings:**
    
    - **Value (Socket - Input/Output):** The angle value (in radians) that is both read from and controlled by the gizmo. The node modifies whatever attribute or value is connected to this socket.
        
    - **Position (Socket - Input):** A vector that defines the center point of the gizmo in the object's local space.
        
    - **Up (Socket - Input):** A vector that defines the orientation of the gizmo's plane (its local Z-axis).
        
    - **Screen Space (Socket - Input):** A boolean. If True, the gizmo maintains a consistent size on the screen regardless of the 3D viewport's zoom level.
        
    - **Radius (Socket - Input):** Controls the size of the gizmo. If Screen Space is active, it's a scaling factor; otherwise, it's the radius in Blender units.
        
    - **Color (Property):** Selects a theme color for the gizmo's appearance in the viewport.
        
    - **Transform (Socket - Output):** A special transform data output that must be joined with the final geometry (using a Join Geometry node) to make the gizmo visible.
        
- **Practical Application:** Imagine you have a procedural model of a security camera on a swivel mount. To aim the camera, you can use a Dial Gizmo. You would position the gizmo at the camera's pivot point. The gizmo's Value output can then be used to drive the Z-axis rotation in a Transform Geometry node that controls the camera's body. After joining the gizmo's Transform output with your camera geometry, a circular handle will appear in the viewport. Dragging this handle allows you to interactively rotate the camera left and right, providing a direct and intuitive way to pose the asset.