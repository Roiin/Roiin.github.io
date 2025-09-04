- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Provides the real-time pixel coordinates of the mouse cursor within the active viewport region. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Mouse X (Socket - Output):** The horizontal position of the mouse cursor in pixels, measured from the left edge of the region.
        
    - **Mouse Y (Socket - Output):** The vertical position of the mouse cursor in pixels, measured from the bottom edge of the region.
        
    - **Region Width (Socket - Output):** The total width of the active viewport region in pixels.
        
    - **Region Height (Socket - Output):** The total height of the active viewport region in pixels.
        
- **Practical Application:** This node is fundamental for creating interactive tools. Imagine building a custom "Surface Painter" tool. The tool would use the Mouse Position output along with a Raycast node to project from the camera's view onto a target mesh. This allows the tool to find the exact 3D position on the mesh that is directly under the user's mouse cursor. That position can then be used to add instances (like rocks or rivets) or to modify attributes (like vertex color), enabling an intuitive, brush-like workflow for the user.