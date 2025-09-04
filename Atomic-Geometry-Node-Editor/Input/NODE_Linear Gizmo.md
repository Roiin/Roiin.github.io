- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Gizmo)
    
- **Core Function:** Creates a linear, arrow-like gizmo in the 3D viewport that allows a user to visually control a single numerical value by dragging along a defined axis.
    
- **Key Properties & Settings:**
    
    - **Value (Socket - Input/Output):** The numerical value that is both read from and controlled by the gizmo's position along its axis.
        
    - **Position (Socket - Input):** A vector that defines the starting point (origin) of the gizmo in the object's local space.
        
    - **Direction (Socket - Input):** A vector that specifies the axis along which the gizmo can be moved.
        
    - **Color (Property):** Selects a theme color for the gizmo's appearance in the viewport.
        
    - **Draw Style (Property):** Allows choosing between different visual styles for the gizmo (e.g., a simple line or an arrow).
        
    - **Transform (Socket - Output):** The gizmo's visual data, which must be joined with the final geometry (using a Join Geometry node) to become visible.
        
- **Practical Application:** This is perfect for controlling linear dimensions like height or length. For example, if you create a procedural wall from a simple plane, you can use an Extrude Mesh node to give it thickness. By connecting the Value output of a Linear Gizmo to the Offset Scale input of the Extrude Mesh node, an arrow gizmo will appear. Dragging this arrow in the viewport will interactively change the wall's thickness, providing an intuitive way to adjust the model's proportions directly.