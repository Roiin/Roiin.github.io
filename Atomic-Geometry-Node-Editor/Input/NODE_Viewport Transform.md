- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Provides the real-time transform matrices and projection state of the active 3D Viewport. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Projection (Socket - Output):** The projection matrix (perspective or orthographic) of the 3D Viewport.
        
    - **View (Socket - Output):** The view matrix, representing the direction and location of the viewport's camera.
        
    - **Is Orthographic (Socket - Output):** A Boolean that is True if the viewport is in an orthographic view (e.g., Top, Front, Right).
        
- **Practical Application:** This is essential for creating "billboard" effects within a custom tool. For example, you could build a tool that places annotation markers in a scene. To ensure these markers are always readable, you want them to face the user. The tool would create a plane for the marker, then use the View output of this node to determine the viewport's rotation. By applying the inverse of this rotation to the plane, the marker will always orient itself to face the user as they orbit and navigate the scene.