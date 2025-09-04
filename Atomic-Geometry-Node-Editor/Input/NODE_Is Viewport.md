- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Outputs a Boolean value that is True when the node tree is being evaluated for the 3D viewport, and False during a final render (e.g., F12).
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Is Viewport (Socket - Output):** A Boolean that is True for viewport display and False for final render.
        
- **Practical Application:** This node is a critical tool for optimizing performance in complex scenes. For example, you can create a procedural rock with a high-resolution displacement effect that is very slow to calculate. By using the Is Viewport output to drive a Switch node, you can set up two paths: a simple, low-polygon version of the rock is sent to the True (Viewport) input of the switch, while the complex, heavily subdivided and displaced version is sent to the False (Render) input. This keeps the viewport fast and interactive while ensuring the final render has maximum detail.