- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Outputs a boolean field that is True for elements (vertices, edges, faces) that are currently selected in Edit Mode. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Selection (Socket - Output):** A Boolean field that is True for selected elements.
        
- **Practical Application:** Imagine building a custom modeling tool called "Create Windows". The workflow is for a user to select several quad faces on the side of a building model in Edit Mode and then run the tool.
    
    1. Inside the tool's node graph, the Selection node is used as the input for a Delete Geometry node set to 'Face' mode. This immediately deletes the selected faces, creating openings for the windows.
        
    2. The output of this Delete Geometry node can then be used to find the boundary edges of the new holes.
        
    3. A Curve to Mesh operation can then be used on these boundary edges to create window frames.  
        This allows the user to interactively and visually define where the windows should be placed simply by selecting faces, making the tool highly intuitive.