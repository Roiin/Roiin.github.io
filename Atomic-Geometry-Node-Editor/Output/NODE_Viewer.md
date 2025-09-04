- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utility
    
- **Core Function:** Allows for the inspection and debugging of geometry and attribute data at any intermediate stage within the node tree, visualizing the data directly in the 3D Viewport and Spreadsheet Editor. **Note: This node is only for use in the modifier context, not for custom tools.**
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The geometry state to be inspected. Its data will be displayed in the Spreadsheet.
        
    - **Value (Socket - Input):** An optional data field (e.g., a noise texture's factor, an object's distance, a calculated index) to visualize on the geometry in the viewport or display as a column in the Spreadsheet.
        
    - **Activation Shortcut (Shift+Ctrl+LMB):** The primary method for using this node. Clicking on any node's output socket with this shortcut will automatically create a Viewer node (if one doesn't exist), connect the socket to it, and make it the active view.
        
    - **Shortcut Assignment (Ctrl + 1-9):** Assigns the currently viewed data to a number key, allowing you to quickly switch between different Viewer nodes or debug points just by pressing the corresponding number (1-9).
        
    - **Domain (Property):** In the sidebar, this allows you to manually specify which attribute domain (Point, Edge, Face, etc.) to inspect when a Value is connected. The 'Auto' setting usually handles this correctly.
        
    - **(This node has no output sockets.)**
        
- **Practical Application:** Imagine you are creating a procedural landscape by displacing a Grid with a Noise Texture via a Set Position node, but the result looks wrong—perhaps the mountains are too spiky or completely flat.
    
    1. To debug, you can hold Shift+Ctrl and click on the Factor output of your Noise Texture node.
        
    2. This instantly connects it to the Value input of the Viewer node and connects the original Grid to the Geometry input.
        
    3. In the 3D Viewport, your flat grid will now be shaded in black and white, directly visualizing the noise pattern. You can immediately see if the noise Scale is wrong (e.g., too large, looking blurry) or if the detail is too high.
        
    4. Simultaneously, in the Spreadsheet Editor, a "Viewer" column will appear, showing the exact numerical value of the noise for every single vertex. This allows you to check if the values are in the expected range (e.g., 0 to 1) before you use them for displacement.  
        By inspecting the data before it affects the final result, you can diagnose problems much more effectively.